# Visit https://github.com/lowlighter/metrics#-documentation for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          #  - public_repo
          #  - read:project
          #  - repo
          #  - read:user
          #  - read:org
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: jd-ashish
          template: classic
          base: ""
          config_timezone: Asia/Calcutta
          plugin_achievements: yes
          plugin_achievements_display: detailed
          plugin_achievements_secrets: yes
          plugin_achievements_threshold: C
          plugin_activity: yes
          plugin_activity_days: 14
          plugin_activity_filter: all
          plugin_activity_limit: 5
          plugin_activity_load: 300
          plugin_activity_visibility: all
          plugin_calendar: yes
          plugin_calendar_limit: 1
          plugin_code: yes
          plugin_code_days: 3
          plugin_code_lines: 12
          plugin_code_load: 400
          plugin_code_visibility: public
          plugin_discussions: yes
          plugin_discussions_categories: yes
          plugin_gists: yes
          plugin_introduction: yes
          plugin_introduction_title: yes
          plugin_isocalendar: yes
          plugin_isocalendar_duration: half-year
          plugin_languages: yes
          plugin_languages_analysis_timeout: 15
          plugin_languages_analysis_timeout_repositories: 7.5
          plugin_languages_categories: markup, programming
          plugin_languages_colors: github
          plugin_languages_limit: 8
          plugin_languages_recent_categories: markup, programming
          plugin_languages_recent_days: 14
          plugin_languages_recent_load: 300
          plugin_languages_sections: most-used
          plugin_languages_threshold: 0%
          plugin_notable: yes
          plugin_notable_from: organization
          plugin_notable_types: commit
          plugin_people: yes
          plugin_people_limit: 24
          plugin_people_size: 28
          plugin_people_types: followers, following
          plugin_projects: yes
          plugin_projects_limit: 4
          plugin_repositories: yes
          plugin_repositories_order: featured, pinned, starred, random
          plugin_skyline: yes
          plugin_skyline_frames: 60
          plugin_skyline_quality: 0.5
          plugin_skyline_settings: {
  "url": "https://skyline.github.com/${login}/${year}",
  "ready": "[...document.querySelectorAll('span')].map(span => span.innerText).includes('Share on Twitter')",
  "wait": 1,
  "hide": "button, footer, a"
}

          plugin_skyline_year: current-year
          plugin_sponsors: yes
          plugin_sponsors_sections: goal, list, about
          plugin_sponsors_size: 24
          plugin_sponsors_title: Sponsor Me!
          plugin_sponsorships: yes
          plugin_sponsorships_sections: amount, sponsorships
          plugin_sponsorships_size: 24
          plugin_starlists: yes
          plugin_starlists_limit: 2
          plugin_starlists_limit_languages: 8
          plugin_starlists_limit_repositories: 2
          plugin_starlists_shuffle_repositories: yes
          plugin_support: yes
          plugin_traffic: yes
