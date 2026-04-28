# SiYuanMemo - Spaced Repetition System Plugin

[简体中文](https://github.com/Dammyxy/siyuan-plugin-siyuanmemo/blob/main/README_zh_CN.md)

Usage:

[Basic feature introduction](https://ld246.com/article/1773097574147)

[Neural Roaming guide](https://ld246.com/article/1773097707973)

[Feedback](https://github.com/Dammyxy/siyuan-plugin-siyuanmemo/issues)

## Changelog

### V0.2.1 (2026-04-28)
- Added AI explanation, AI card creation, AI Workbench, general chat, user Skills, tool calls and approvals, and session history. These can be configured in settings and opened from the upper-right corner of the review interface.
- Added Excerpt and progressive reading: document split, `Alt+X` excerpting, Topic excerpts, continuing cloze card creation under Topics, excerpt records, source lineage, and Excerpts and Sync settings.
- Reworked the SRS v2 scheduler: six-queue commit semantics, learning/relearning steps, new-card/review limits, FilterGroup preview-only behavior, and independent FinalDrill drill logs.
- Improved the review experience: review entry points, tab/dialog/split-screen restoration, queue switching, loop prevention, reduced card-switch flicker, card-switch preloading, formula cloze stability, and special-card renderer stability.
- Improved queues and the SRS Browser: FilterGroup, Retrieval Practice, Incremental Learning, manual adds, precise same-block multi-card review, SQL search filtering to real cards, and context menus after SQL search.
- Strengthened Neural Roaming: virtual nodes, associated real-card follow-ups, trace/convergence nodes, paged history, Wake/trace display, and AI access to roaming context.
- Fixed the CDF card creation path: concept-card reuse, descriptor cue-answer semantics, multiline CDF, concept definition cards, native cloze routing, duplication, and idempotency issues.
- Added the Arena prototype, disabled by default to avoid affecting normal review.
- Added many UI and stability fixes: settings, AI settings, review interface, browser toolbar, title bar, buttons, menus, Riff sync, storage merge, and startup initialization.

### v0.1.7 (2026-03-18)
- Fixed the issue where the plugin could not initialize.
- Added convergence nodes to Neural Roaming trajectory paths, so repeatedly activated nodes during spreading activation are visible.

### v0.1.6 (2026-02-15)
- Optimized the performance of the SRS Browser and automatic card entry. Batch operations now need a short wait.

This plugin lets you:

1. Better use the **Spaced Repetition System** to drive two strategies, **retrieval practice** and **drill practice**, for memorizing anything.
2. Use SiYuan's **bidirectional links** and **Spaced Repetition System** to deeply connect rote-memorized information with the knowledge in your brain, promote transfer learning and elaborative encoding, wire up your brain, keep knowledge from becoming isolated, and build your own knowledge system.

## Feature Overview

1. **Practice System:** two practice strategies and algorithms

   - Retrieval practice driven by the spaced repetition algorithm (FSRS)
   - Drill practice driven by the SuperMemo Final Drill dynamic algorithm
2. **Neural Roaming System:** combines SiYuan bidirectional links with SuperMemo neural review, adding an intelligent brain to the Spaced Repetition System so you can build and retrieve your tacit knowledge, support inquiry-based learning, and let knowledge grow freely.
3. **Concept/Descriptor Framework (CDF):** a RemNote-style template card creation system that helps you quickly break down information and create cards according to focused, precise, and consistent card-making principles.
4. **Comprehensive card creation features**:

   - Formula card creation
   - Image card creation
   - Ordered-list template cards (with progressive hints during review)
   - Unordered-list template cards (with summary hints during review)
   - Concept/Descriptor Framework template cards
   - Listener-based card creation

     - Symbol-listener card creation
     - Also listens to SiYuan's native **Quick Make Card**. After clicking **Quick Make Card**, it automatically recognizes the card format, converts it into a card type supported by this plugin, and syncs it to the plugin.
   - Decouples SiYuan blocks from flashcards, so one block can produce multiple cards.
   - Does not pollute SiYuan's native review interface; the newly added card types have their own review interfaces.
5. **Two review entry points**

   - Traditional queue-based review entry

     - Enter review from the right-click menu of the plugin top-bar button.
     - Enter review from the browser **Practice** button.
     - Enter review from the **/ menu**.
     - Enter review from the command palette.
   - RemNote-style block-level review entry for precise review granularity

     - In the document block menu, review all flashcards in the current document block and its child blocks.
     - In other block menus, review all flashcards in the current block and its child blocks.
6. **SuperMemo-style SRS Browser**

   - Manage your flashcards in a table view.
7. **Five queues**

   - Traditional Retrieval Practice queue
   - Incremental Learning queue inspired by SuperMemo
   - Fallback Final Drill queue
   - Neural Roaming queue combining bidirectional links and neural review
   - Filtered Review queue for precisely adjusting review scope during review
8. **SuperMemo-style queue management**

   - Sort review queues so you can review cards in your preferred order.
   - Insert selected cards into any queue.
   - During review, insert cards into any position in the queue or schedule them to the future.
9. **Card planning features for a better review experience**

   - Postpone
   - Advance
   - Spread

When SiYuan was about to build flashcards, I had these ideas in mind. Now the timing is right, so I built them first. This plugin has just reached the second stage of flashcards, and there is still a lot to improve.
