# 📊 Event Schema Design - KIU Connect (MVP v1.0)

**Team:** KIU Student Well-being Research Team
**Date:** October 31, 2025
**Product:** KIU Connect - Student Well-being & Peer Support Platform
**Version:** 1.0 (MVP)

## Overview
This document defines the event schema for KIU Connect's analytics instrumentation. Every user action we want to track must be captured as an event with standardized properties.

**Purpose:**
* Enable data-driven product decisions to reduce student isolation and burnout.
* Track our **North Star Metric (Weekly Active Check-ins)** and **AARRR funnel**.
* Identify friction points preventing students from seeking support.
* Measure feature adoption (peer matching, resource usage, community engagement).
* Validate our hypothesis that anonymous peer support reduces stigma.

---

## 🏷️ Event Naming Conventions
**Format:** `object_action` (snake_case)

| Status | Example | Rule Violated |
| :--- | :--- | :--- |
| **✅** | `check_in_completed` | N/A |
| **✅** | `user_signup_completed` | N/A |
| **✅** | `peer_match_found` | N/A |
| **❌** | `CheckInCompleted` | wrong case |
| **❌** | `complete_check_in` | wrong order ([object]_[action]) |
| **❌** | `check_in_complete` | inconsistent verb tense |

**Rules:**
* Always **lowercase with underscores** (`snake_case`).
* Format: `[object]_[action]` (**noun first, verb second**).
* Use **past tense** for completed actions: `_completed`, `_created`, `_found`.
* Use **present tense** for ongoing: `_started`, `_viewed`, `_requested`.
* Be specific: `check_in_started` not `action_performed`.

---

## 🔑 Standard Properties (All Events)
These properties **MUST** be included with every event:

| Property Name | Type | Description | Example |
| :--- | :--- | :--- | :--- |
| `event_id` | `string (UUID)` | Unique identifier for this event | `"550e8400-e29b-41d4-a716-446655440000"` |
| `user_id` | `string (UUID)` | Anonymous unique identifier (never real student ID) | `"anon_user_a7b3c9d2"` |
| `timestamp` | `ISO 8601 datetime` | When the event occurred (UTC) | `"2025-10-30T14:23:45Z"` |
| `session_id` | `string (UUID)` | Current user session | `"session_67890abc"` |
| `platform` | `enum` | Where event occurred | `"web"`, `"ios"`, `"android"` |
| `app_version` | `string` | Application version | `"1.0.0"` |
| `environment` | `enum` | Deployment environment | `"production"`, `"staging"`, `"development"` |

> **CRITICAL PRIVACY NOTE:**
> `user_id` is an **anonymous UUID** generated at signup, **NOT** the student's KIU ID number or email. We **never** track personally identifiable information (PII).

---

## 🎯 Core Events (8 Required for MVP)

### Event 1: `user_signed_up`
* **When it fires:** User successfully completes signup and anonymous account is created.
* **Why we track it:** Measures **Acquisition** stage in AARRR; validates our ability to reach stressed students.
* **Custom Properties:**

| Property Name | Type | Required | Description | Example Values |
| :--- | :--- | :--- | :--- | :--- |
| `signup_method` | `enum` | Yes | How user signed up | `"email"`, `"google"`, `"anonymous"` |
| `user_type` | `enum` | Yes | Type of account created | `"student"`, `"faculty"` (MVP: students only) |
| `referred_by_peer` | `boolean` | Yes | Whether user used peer referral link | `true`, `false` |
| `onboarding_completed` | `boolean` | Yes | Whether user finished intro flow immediately | `true`, `false` |
| `time_to_complete_seconds` | `integer` | Yes | Seconds from landing to signup completion | `45`, `120`, `300` |

**Example Event Payload:**
```json
{
  "event_name": "user_signed_up",
  "event_id": "550e8400-e29b-41d4-a716-446655440000",
  "user_id": "anon_user_a7b3c9d2",
  "timestamp": "2025-10-30T14:23:45Z",
  "session_id": "session_67890abc",
  "platform": "web",
  "app_version": "1.0.0",
  "environment": "production",
  "signup_method": "email",
  "user_type": "student",
  "referred_by_peer": false,
  "onboarding_completed": true,
  "time_to_complete_seconds": 87
}
Event 2: check_in_startedWhen it fires: User opens the emotional check-in modal/screen.Why we track it: Measures intent to complete check-in; helps calculate completion rate (check-in funnel).Custom Properties:Property NameTypeRequiredDescriptionExample Valuesentry_pointenumYesWhere user initiated check-in"home_dashboard", "notification", "peer_prompt", "resource_page"time_of_dayintegerYesHour of day (0-23) when check-in started9, 14, 22days_since_last_checkinintegerNoDays since user's previous check-in (null if first)1, 3, 7, nullprompt_typeenumNoIf triggered by prompt/reminder"daily_reminder", "stress_alert", "peer_invitation", nullExample Event Payload:JSON{
  "event_name": "check_in_started",
  "event_id": "abc-123-def-456",
  "user_id": "anon_user_a7b3c9d2",
  "timestamp": "2025-10-31T10:15:30Z",
  "session_id": "session_67890abc",
  "platform": "web",
  "app_version": "1.0.0",
  "environment": "production",
  "entry_point": "home_dashboard",
  "time_of_day": 10,
  "days_since_last_checkin": 2,
  "prompt_type": null
}
Relationship: Followed by: check_in_completed OR check_in_abandoned.Conversion metric: check_in_completed / check_in_started = Check-in Completion Rate (target: >85%).Event 3: check_in_completedWhen it fires: User successfully submits emotional check-in form.Why we track it: POWERS OUR NORTH STAR METRIC (Weekly Active Check-ins). Also measures Activation for new users.Custom Properties:Property NameTypeRequiredDescriptionExample Valuesmood_selectedenumYesEmotional state chosen"happy", "neutral", "stressed", "overwhelmed", "anxious"stress_levelintegerYesSelf-reported stress (1-10 scale)1 (low) to 10 (extreme)completion_statusenumYesHow check-in was completed"completed", "partial", "abandoned"time_taken_secondsintegerYesTime from start to submission30, 90, 240support_requestedbooleanYesWhether user requested peer support after check-intrue, falseis_first_checkinbooleanYesWhether this is user's first-ever check-intrue, falseExample Event Payload:JSON{
  "event_name": "check_in_completed",
  "event_id": "xyz-789-uvw-012",
  "user_id": "anon_user_a7b3c9d2",
  "timestamp": "2025-10-31T10:17:15Z",
  "session_id": "session_67890abc",
  "platform": "web",
  "app_version": "1.0.0",
  "environment": "production",
  "mood_selected": "stressed",
  "stress_level": 7,
  "completion_status": "completed",
  "time_taken_seconds": 105,
  "support_requested": true,
  "is_first_checkin": false
}
Relationship: Follows: check_in_started.North Star Metric Calculation: COUNT(DISTINCT user_id WHERE event='check_in_completed' AND timestamp WITHIN last_7_days).Event 4: peer_match_requestedWhen it fires: User clicks "Find a Peer" or requests peer matching after check-in.Why we track it: Measures engagement with core feature; validates hypothesis that students want anonymous peer connection.Custom Properties:Property NameTypeRequiredDescriptionExample Valuesmatch_preferencesarrayYesUser's matching preferences (up to 5)["similar_mood", "same_major", "available_now"]availabilityenumYesWhen user is available to connect"now", "within_1_hour", "today", "this_week"triggered_byenumYesWhat prompted the request"check_in_prompt", "manual_search", "notification"current_moodenumNoUser's current mood (if from check-in)"happy", "stressed", "anxious", etc.stress_levelintegerNoUser's current stress level (if from check-in)1 to 10Example Event Payload:JSON{
  "event_name": "peer_match_requested",
  "event_id": "req-456-match-789",
  "user_id": "anon_user_a7b3c9d2",
  "timestamp": "2025-10-31T10:18:00Z",
  "session_id": "session_67890abc",
  "platform": "web",
  "app_version": "1.0.0",
  "environment": "production",
  "match_preferences": ["similar_mood", "same_major"],
  "availability": "now",
  "triggered_by": "check_in_prompt",
  "current_mood": "stressed",
  "stress_level": 7
}
Relationship: Followed by: peer_match_found OR peer_match_not_found.Event 5: peer_match_foundWhen it fires: System successfully matches user with an available peer.Why we track it: Measures success rate of peer matching; critical for Retention.Custom Properties:Property NameTypeRequiredDescriptionExample Valuesmatch_methodenumYesAlgorithm used for matching"mood_based", "major_based", "stress_level"shared_interests_countintegerYesNumber of matching preferences0, 1, 2, 3response_time_msintegerYesMilliseconds to find match1200, 5000, 30000match_quality_scorefloatYesAlgorithm confidence (0.0-1.0)0.85, 0.92peer_availabilityenumYesHow soon peer is available"now", "within_1_hour", "today"Example Event Payload:JSON{
  "event_name": "peer_match_found",
  "event_id": "match-found-123",
  "user_id": "anon_user_a7b3c9d2",
  "timestamp": "2025-10-31T10:18:03Z",
  "session_id": "session_67890abc",
  "platform": "web",
  "app_version": "1.0.0",
  "environment": "production",
  "match_method": "mood_based",
  "shared_interests_count": 2,
  "response_time_ms": 3200,
  "match_quality_score": 0.87,
  "peer_availability": "now"
}
Success metric: peer_match_found / peer_match_requested (target: >70%).Event 6: resource_viewedWhen it fires: User clicks on and opens a well-being resource (article, video, exercise, counseling info).Why we track it: Measures engagement with support content; identifies which resources are most helpful.Custom Properties:Property NameTypeRequiredDescriptionExample Valuesresource_idstringYesUnique identifier for resource"res_breathing_exercise_01", "res_counseling_info"resource_typeenumYesCategory of resource"breathing_exercise", "article", "video", "counseling_info"resource_categoryenumYesWell-being area addressed"stress_management", "academic_support", "mental_health"sourceenumYesWhere user found this resource"home_feed", "search", "peer_recommendation"user_mood_contextenumNoUser's mood when viewing (if available)"stressed", "anxious", etc.Example Event Payload:JSON{
  "event_name": "resource_viewed",
  "event_id": "res-view-456",
  "user_id": "anon_user_a7b3c9d2",
  "timestamp": "2025-10-31T11:30:00Z",
  "session_id": "session_67890abc",
  "platform": "web",
  "app_version": "1.0.0",
  "environment": "production",
  "resource_id": "res_breathing_exercise_01",
  "resource_type": "breathing_exercise",
  "resource_category": "stress_management",
  "source": "post_checkin_suggestion",
  "user_mood_context": "stressed"
}
Event 7: community_post_createdWhen it fires: User creates a post in the anonymous community feed.Why we track it: Measures community engagement; validates hypothesis that students want to share experiences anonymously.Custom Properties:Property NameTypeRequiredDescriptionExample Valuespost_typeenumYesType of post created"question", "experience_share", "encouragement"post_categoryenumYesTopic area"academic_stress", "social_connection", "mental_health"anonymity_levelenumYesLevel of anonymity chosen"fully_anonymous", "class_year_shown", "major_shown"contains_trigger_warningbooleanYesWhether post includes content warningtrue, falsecharacter_countintegerYesLength of post content50, 200, 500Example Event Payload:JSON{
  "event_name": "community_post_created",
  "event_id": "post-789-xyz",
  "user_id": "anon_user_a7b3c9d2",
  "timestamp": "2025-10-31T14:45:20Z",
  "session_id": "session_67890abc",
  "platform": "web",
  "app_version": "1.0.0",
  "environment": "production",
  "post_type": "experience_share",
  "post_category": "academic_stress",
  "anonymity_level": "fully_anonymous",
  "contains_trigger_warning": false,
  "character_count": 287
}
Privacy note: We track post metadata only, NEVER the actual post content.Event 8: user_returned_day_7When it fires: Automated event triggered when user completes any action on Day 7 after signup.Why we track it: KEY RETENTION METRIC for AARRR funnel; measures product stickiness.Custom Properties:Property NameTypeRequiredDescriptionExample Valuessignup_cohortstringYesWeek user signed up"2025_week_44", "2025_week_45"checkins_completedintegerYesTotal check-ins in first 7 days0, 3, 7, 12peer_matches_initiatedintegerYesPeer connections made in first 7 days0, 1, 2resources_viewedintegerYesResources opened in first 7 days0, 2, 5community_engagementenumYesLevel of community participation"none", "viewer", "participant"activation_achievedbooleanYesWhether user completed first check-in within 48htrue, falseExample Event Payload:JSON{
  "event_name": "user_returned_day_7",
  "event_id": "retention-day7-123",
  "user_id": "anon_user_a7b3c9d2",
  "timestamp": "2025-11-07T14:23:45Z",
  "session_id": "session_new_789",
  "platform": "web",
  "app_version": "1.0.0",
  "environment": "production",
  "signup_cohort": "2025_week_44",
  "checkins_completed": 5,
  "peer_matches_initiated": 1,
  "resources_viewed": 3,
  "community_engagement": "viewer",
  "activation_achieved": true
}
Implementation note: Backend cron job checks daily at 9 AM UTC for users who signed up exactly 7 days ago and logged in today.📈 Event-to-Metric MappingNorth Star MetricOur NSM: Weekly Active Check-insDefinition: Count of unique users who completed at least one emotional check-in in the last 7 days.Events that power it: check_in_completed.Calculation:SQLSELECT COUNT(DISTINCT user_id)
FROM events
WHERE event_name = 'check_in_completed'
  AND completion_status = 'completed'
  AND timestamp >= NOW() - INTERVAL '7 days'
Target for Week 10: 150 weekly active check-ins.AARRR Funnel MappingAARRR StageEventsMetric CalculationTargetAcquisitionuser_signed_upSignups per week50/week by Week 10Activationcheck_in_completed (where is_first_checkin=true within 48h of signup)first_checkins_within_48h / signups60%Retentionuser_returned_day_7day_7_active_users / activated_users40%Referraluser_signed_up (where referred_by_peer=true) OR peer_match_requestedreferred_signups / total_signups15%RevenueN/AN/A (free platform for MVP)N/A💻 Implementation GuidelinesWhere to Instrument EventsEvent NameLocationNotesuser_signed_upFrontendSignup form submissioncheck_in_startedFrontendCheck-in modal opencheck_in_completedFrontendCheck-in form submissionpeer_match_requestedFrontend"Find Peer" button clickresource_viewedFrontendResource card clickcommunity_post_createdFrontendPost submissionpeer_match_foundBackendMatching algorithm completesuser_returned_day_7BackendCron job (daily at 9 AM UTC)Rule of Thumb: Track events where they happen - UI interactions in frontend, system operations in backend.Code Example (React + Mixpanel)JavaScript// src/utils/analytics.js
import mixpanel from 'mixpanel-browser';

// Initialize on app load
mixpanel.init(import.meta.env.VITE_MIXPANEL_TOKEN, {
  debug: import.meta.env.VITE_ENV === 'development',
  track_pageview: false,
  persistence: 'localStorage',
  ip: false // Don't track IP addresses (CRITICAL PRIVACY)
});

// Standard properties added to every event
function getStandardProps() {
  return {
    event_id: crypto.randomUUID(),
    user_id: getAnonymousUserId(), // Retrieves UUID from localStorage
    timestamp: new Date().toISOString(),
    session_id: getSessionId(),
    platform: 'web',
    app_version: import.meta.env.VITE_APP_VERSION,
    environment: import.meta.env.VITE_ENV
  };
}

// Main tracking function
export function trackEvent(eventName, customProperties = {}) {
  try {
    // Validate no PII
    validateNoPII(customProperties);
        
    // Merge standard + custom properties
    const eventPayload = {
      ...getStandardProps(),
      ...customProperties
    };
        
    // Send to Mixpanel
    mixpanel.track(eventName, eventPayload);
        
    // Log in development
    if (import.meta.env.VITE_ENV === 'development') {
      console.log('📊 Analytics:', eventName, eventPayload);
    }
  } catch (error) {
    console.error('Analytics error:', error);
    // Don't block user experience
  }
}

// Usage in component
function CheckInModal() {
  const handleOpen = () => {
    trackEvent('check_in_started', {
      entry_point: 'home_dashboard',
      time_of_day: new Date().getHours(),
      days_since_last_checkin: getDaysSinceLastCheckIn()
    });
  };
    
  const handleSubmit = (mood, stressLevel) => {
    trackEvent('check_in_completed', {
      mood_selected: mood,
      stress_level: stressLevel,
      completion_status: 'completed',
      time_taken_seconds: getTimeSinceOpen(),
      support_requested: false,
      is_first_checkin: isFirstCheckIn()
    });
  };
    
  return (
    <Modal onOpen={handleOpen}>
      <CheckInForm onSubmit={handleSubmit} />
    </Modal>
  );
}
🔒 Privacy & CompliancePII (Personally Identifiable Information) RulesNEVER include in event properties:❌ Email addresses, Phone numbers❌ Real names (first, last, or full)❌ Student ID numbers (e.g., 123456)❌ IP addresses (disabled in Mixpanel config)❌ User-generated content (check-in text, post content, messages)Always use instead:✅ Anonymous UUIDs: "anon_user_a7b3c9d2"✅ Enum values only: "stressed" not free text✅ Aggregated/categorical data: "major_category" not specific identityData RetentionRaw events: 90 days (Mixpanel free tier limit).Aggregated metrics: Indefinitely (no PII in aggregations).Deletion policy: Users can request complete data deletion via Settings → Privacy → Delete My Data (processed within 48 hours).Compliance: GDPR-compliant; Anonymous by design protects student privacy.
