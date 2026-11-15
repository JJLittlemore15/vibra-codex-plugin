---
name: brainstorm-reels
description: Propose five concrete padel reel ideas built from the user's own Vibra Clips and what is trending on Vibra Radar. Use when the user asks for reel ideas, what to post, content ideas, or to brainstorm from Vibra Radar or their clips.
---

# Brainstorm reels from Vibra Clips and Vibra Radar

The Vibra tools come from this plugin's `vibra` MCP server and are read-only. If they are missing or
say the user is not signed in, use the `setup` skill and stop.

1. Call `reel_playbook` first and follow it over anything here.
2. Call `top_radar_reels`. Read why each reel scored and its craft breakdown; look for patterns
   that repeat.
3. Call `list_my_labels`, then `find_my_clips` (prefer labelled, unused clips; narrow by the user's
   focus if given).
4. Propose **five** ideas, each makeable from clips the user really has - never invent clips. For
   each: title, the clips (label, match date, `item_id`, seconds), the hook in the first 1-2
   seconds, the order and payoff, target length, a caption idea, and one line on why it should work.
   Use Radar reels for craft only; never copy them.
5. If there are too few clips for five, say so, propose what the clips support, and suggest what to
   film or label next.
6. Ask which idea to make, then use the `make-reel` skill with the choices already filled in.

Never post or share anything.
