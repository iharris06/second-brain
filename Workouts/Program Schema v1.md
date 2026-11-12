{
  "programId": "tactical_longevity_5_pillars_190",
  "programName": "Tactical Longevity - 5 Pillars Edition",
  "version": "1.2.0",
  "targetMetrics": {
    "targetWeightLbs": 190.0,
    "targetBodyFatPercentage": 15.0,
    "dailyCalorieTargetKcal": 2300,
    "dailyMacrosGrams": {
      "protein": 170,
      "carbs": 260,
      "fats": 65
    }
  },
  "weeklySchedule": [
    {
      "dayNumber": 1,
      "dayName": "Monday",
      "focus": "Pillar 1: Strength (Upper Body Push/Pull) & Pillar 4: Mobility",
      "location": "Home",
      "appleWatchWorkoutType": "Traditional Strength Training",
      "estimatedDurationMinutes": 40,
      "completed": false,
      "phases": [
        {
          "phaseName": "Pillar 4 & 5: Daily Longevity Warm-up",
          "phaseOrder": 1,
          "exercises": [
            { "id": "core_360_breath", "name": "Transverse Activation (360° Breath)", "durationSeconds": 60, "notes": "Anti-bulge focus." },
            { "id": "mobility_thoracic_bridge", "name": "Thoracic Bridges (Spine & Shoulders)", "sets": 2, "reps": 8, "notes": "Attia Mobility Target: Spine and shoulder opening." },
            { "id": "core_dead_bug", "name": "Dead Bugs (TVA Focus)", "sets": 2, "reps": 10 },
            { "id": "core_hard_style_plank", "name": "Hard-Style Plank", "sets": 2, "durationSeconds": 20 }
          ]
        },
        {
          "phaseName": "Pillar 1: Progressive Overload Strength (Superset)",
          "phaseOrder": 2,
          "exercises": [
            { "id": "kb_overhead_press", "name": "Kettlebell Overhead Press", "supersetGroup": "A", "sets": 5, "repsTarget": "6-8", "prescribedWeightLbs": 35.0, "restSeconds": 60, "tracking": { "setsCompleted": [] } },
            { "id": "weighted_pull_up", "name": "Pull-ups / Chin-ups", "supersetGroup": "A", "sets": 5, "repsTarget": "sub-max", "prescribedWeightLbs": 15.0, "restSeconds": 60, "tracking": { "setsCompleted": [] } }
          ]
        },
        {
          "phaseName": "Deltoid & Hypertrophic Volume (Tri-set)",
          "phaseOrder": 3,
          "exercises": [
            { "id": "kb_deficit_pushup", "name": "Kettlebell Deficit Push-ups", "supersetGroup": "B", "sets": 3, "repsTarget": "max_clean", "tracking": { "setsCompleted": [] } },
            { "id": "db_lateral_raise", "name": "Dumbbell Lateral Raises", "supersetGroup": "B", "sets": 3, "repsTarget": "15-20", "prescribedWeightLbs": 10.0, "tracking": { "setsCompleted": [] } },
            { "id": "db_rear_delt_fly", "name": "Dumbbell Rear Delt Flies", "supersetGroup": "B", "sets": 3, "repsTarget": "15", "prescribedWeightLbs": 10.0, "tracking": { "setsCompleted": [] } }
          ]
        }
      ]
    },
    {
      "dayNumber": 2,
      "dayName": "Tuesday",
      "focus": "Pillar 1: Explosive Power & Pillar 5: Neuromuscular Balance",
      "location": "Home/Yard",
      "appleWatchWorkoutType": "Functional Strength Training",
      "estimatedDurationMinutes": 35,
      "completed": false,
      "phases": [
        {
          "phaseName": "Pillar 4 & 5: Warm-up & Balance Activation",
          "phaseOrder": 1,
          "exercises": [
            { "id": "core_360_breath", "name": "Transverse Activation (360° Breath)", "durationSeconds": 60 },
            { "id": "balance_single_leg_stand", "name": "Single-Leg Stand (Eyes Closed)", "sets": 2, "durationSeconds": 30, "notes": "Attia Pillar 5: Neuromuscular control drill." },
            { "id": "mobility_ankle_rock", "name": "Ankle Mobility Drills", "sets": 2, "reps": 10, "notes": "Attia Mobility Target: Ankles (critical for soft volleyball landing)." }
          ]
        },
        {
          "phaseName": "Agility & Triple-Extension Plyometrics",
          "phaseOrder": 2,
          "exercises": [
            { "id": "agility_ladder", "name": "Agility Ladder Drills", "durationSeconds": 300 },
            { "id": "plyo_vertical_jump", "name": "Vertical Max-Effort Jumps", "sets": 5, "reps": 3, "restSeconds": 45, "tracking": { "setsCompleted": [] } }
          ]
        },
        {
          "phaseName": "Conditioning EMOM",
          "phaseOrder": 3,
          "exercises": [
            { "id": "kb_snatch_emom", "name": "Kettlebell Snatches (EMOM)", "durationSeconds": 600, "prescribedWeightLbs": 35.0, "notes": "10 minutes total. High-intensity hip extension.", "tracking": { "intervalsCompleted": 0 } }
          ]
        }
      ]
    },
    {
      "dayNumber": 3,
      "dayName": "Wednesday",
      "focus": "Pillar 4: Mobility & Pillar 5: Balance (Active Recovery Skill Day)",
      "location": "Home",
      "appleWatchWorkoutType": "Flexibility",
      "estimatedDurationMinutes": 25,
      "completed": false,
      "phases": [
        {
          "phaseName": "Pillar 4 & 5: Dedicated Longevity Skills",
          "phaseOrder": 1,
          "exercises": [
            { "id": "core_360_breath", "name": "Transverse Activation (360° Breath)", "durationSeconds": 60 },
            { "id": "balance_sl_slings", "name": "Single-Leg Kettlebell Slings", "sets": 3, "reps": 10, "prescribedWeightLbs": 15.0, "notes": "Pass a light KB hand-to-hand around your body while standing on one leg." },
            { "id": "movnat_bear_crawl", "name": "Bear Crawl (Core & Shoulder Stability)", "sets": 4, "distanceFeet": 30 },
            { "id": "mobility_hamstring_hinge", "name": "Dynamic Hamstring Flossing", "sets": 2, "reps": 12, "notes": "Attia Mobility Target: Hamstrings and lower back relief." },
            { "id": "movnat_dead_hang", "name": "Dead Hang from Pull-up Bar", "sets": 3, "repsTarget": "max_time" }
          ]
        }
      ]
    },
    {
      "dayNumber": 4,
      "dayName": "Thursday",
      "focus": "Pillar 1 & 5: Unilateral Lower Body Overload & Hinge Mechanics",
      "location": "Home",
      "appleWatchWorkoutType": "Traditional Strength Training",
      "estimatedDurationMinutes": 45,
      "completed": false,
      "phases": [
        {
          "phaseName": "Pillar 4 & 5: Dynamic Loading Warm-up",
          "phaseOrder": 1,
          "exercises": [
            { "id": "core_360_breath", "name": "Transverse Activation (360° Breath)", "durationSeconds": 60 },
            { "id": "mobility_deep_squat_sit", "name": "Deep Squat Sit & Hip Prying", "durationSeconds": 60 },
            { "id": "core_bird_dog", "name": "Bird-Dogs", "sets": 2, "reps": 10 },
            { "id": "core_hard_style_plank", "name": "Hard-Style Plank", "sets": 2, "durationSeconds": 20 }
          ]
        },
        {
          "phaseName": "Pillar 1 & 5: Single-Leg Pistol Squat Progression",
          "phaseOrder": 2,
          "exercises": [
            { 
              "id": "unilateral_pistol_progression", 
              "name": "Pistol Squat Progression", 
              "sets": 3, 
              "repsTarget": "5-8 per leg", 
              "notes": "Weeks 1-4: Bench/Box Pistol. Weeks 5-8: Airborne Squat. Weeks 9+: Counterbalanced Floor Pistol. Focus on stabilizing the ankle and knee completely.",
              "tracking": { "setsCompleted": [] } 
            }
          ]
        },
        {
          "phaseName": "Pillar 1: Bilateral Loading & Power",
          "phaseOrder": 3,
          "exercises": [
            { "id": "kb_double_front_squat", "name": "Double Kettlebell Front Squats", "sets": 3, "reps": 10, "prescribedWeightLbs": 70.0, "notes": "Two 35lb bells. Squeeze tight to chest.", "tracking": { "setsCompleted": [] } }
          ]
        },
        {
          "phaseName": "Pillar 1: Hinge Pattern Power EMOM",
          "phaseOrder": 4,
          "exercises": [
            { "id": "kb_hardstyle_swing_emom", "name": "Hard-Style Kettlebell Swings (EMOM)", "durationSeconds": 600, "prescribedWeightLbs": 53.0, "notes": "10-12 reps per minute. Snap the hips violently.", "tracking": { "intervalsCompleted": 0 } }
          ]
        }
      ]
    },
    {
      "dayNumber": 5,
      "dayName": "Friday or Saturday",
      "focus": "Pillar 3: Cardiorespiratory Longevity Engine (Norwegian 4x4 Focus)",
      "location": "Gym",
      "appleWatchWorkoutType": "Indoor Rowing",
      "estimatedDurationMinutes": 35,
      "completed": false,
      "phases": [
        {
          "phaseName": "Pillar 3: High-Intensity Cardiovascular Overload",
          "phaseOrder": 1,
          "exercises": [
            { 
              "id": "norwegian_4x4_row_or_run", 
              "name": "Norwegian 4x4 Interval Protocol", 
              "durationSeconds": 1680, 
              "notes": "Perform on Rower or Treadmill: 4 mins at Max Sustainable High Intensity (Zone 4/5, ~85-95% Max HR) followed by 3 mins of active recovery/easy movement. Repeat 4 times total.",
              "tracking": { "intervalsCompleted": 0 } 
            }
          ]
        }
      ]
    }
  ]
}