# PinBuilds

PinBuilds creates Pinterest pins from a blog post or a Shopify/Etsy product and schedules them to the user's Pinterest boards. The `pinbuilds` MCP server signs the user in to their PinBuilds account (OAuth) on first use.

## Rules

- Generation uses the user's monthly PinBuilds pins, and scheduling creates real Pinterest posts. Confirm with the user before calling `generate_pins_for_url`, `generate_and_schedule_post`, `submit_generation_job` or `schedule_generated_pins`.
- Call `get_usage` before generating. Stop if the plan has ended or too few pins are left.
- A URL must belong to one of the user's site profiles (`list_profiles`). If none matches, tell the user to add the site at https://pinbuilds.com/settings.
- To find posts that still need pins, use `check_article_status`.
- To generate and schedule in one step, use `generate_and_schedule_post` with `scheduleConfig.timezone` set to the user's IANA timezone. Pins per day and posting hours are set in PinBuilds.
- Read-only tools that use no pins: `get_usage`, `list_profiles`, `list_boards`, `list_generated_pins`, `check_article_status`, `get_generation_job_status`.
- Report results plainly: pins made, pins scheduled and from which date, and any errors. Pins can be reviewed at https://pinbuilds.com/history and https://pinbuilds.com/scheduler.
