This plugin enhances/refines Siyuan's Spaced Repetition System (SRS). I had ideas related to this back when Siyuan was just starting to implement flashcards. Now that the time is right, I have brought it to life.

This plugin has just reached the "Phase 2" of flashcard development and still has many areas for improvement. Its main features are as follows:

# SRS Browser

![image](https://raw.githubusercontent.com/Dammyxy/siyuan-plugin-siyuanmemo/main/assets/image-20260217135755-mcan1zg.png)

* **Right Side (Preview Pane):** Previews the block corresponding to the flashcard. It is locked by default; double-click to unlock.
* **Bottom Left (Document Pane):** Displays the document blocks where all flashcards are located. It focuses dynamically based on search results, conditional filters, or the current queue, assisting in flashcard management.
* **Top Left (Queue Pane):** Clicking into a queue displays the flashcards within that specific queue. You can right-click to manage them, including Remove, Sort, Postpone, and Advance.

# Four Types of Flashcards

## Practice (Item Card)

* **Explanation:** The generalized flashcard. Question on the front, Answer on the back. This is the purest form of **Retrieval Practice**.
* **How to create:**
* Inside the plugin, after "Auto Card Creation" runs, cards with a "back-side answer" are automatically identified as **Items**.
* Auto Card Creation includes:
* Siyuan's native flashcards.
* Plugin's Template Cards.
* Plugin's Symbol Cards.




* You can also manually mark a card type as "Item" in the Browser.



## Material (Topic Card)

* **Explanation:** Reading material.
* **How to create:**
* After "Auto Card Creation" runs, cards *without* a "back-side answer" are identified as **Topics**. You can also manually mark them in the Browser.



## Definition (Descriptor Card)

* **Explanation:**
* Simply put, this is **Template Card Creation**. I first encountered this concept in [The Two Approaches to Spaced Repetition Software](https://zhuanlan.zhihu.com/p/396445859) by Jarrett Ye.
* It originates from RemNote's **CDF (Concept/Descriptor Framework)**. This is a highly formalized knowledge decomposition tool.


* **Essence:**
* It’s not just for the convenience of filling out tables (like SuperTags); it is a form of **"Attention Programming"** that introduces an expert perspective. Just like an AI Prompt, an expert guides your attention via the *Descriptors* in CDF, helping you identify the useful parts of information. It is equivalent to wearing a "persona mask" to reuse an expert's experience.
* For students, this formalized (structured) tool is very convenient.


* **How to create:**
* You need to use the "Transitive Bidirectional Link" syntax, which is demonstrated below.



## Concept (Concept Card)

* **Explanation:**
* This is *not* the "Concept" from the CDF framework, but the "Concept" used for **Neural Review** in SuperMemo. In this plugin, the Concept is the core node of the **Neural Roaming** queue.


* Corresponding to bidirectional links, a Concept Card is essentially a **Document Block** in Siyuan.
* **How to create:**
* Click on the document block icon (gutter icon), and you will see these two buttons:
* Make as Concept Card and Join Queue.
* Make as Concept Card and Roam Immediately.





# Five Types of Queues

## Three Dynamic Queues

### Retrieval Practice

* **Card Source:** Fetches **Items** and **Descriptors** that are due today or manually added to the queue.
* **Algorithm:** Driven by the **FSRS** algorithm.

### Incremental Learning

* **Card Source:** Fetches **all types** of cards that are due today or manually added to the queue.
* **Algorithm:** **Items** and **Descriptors** are driven by FSRS; **Topics** and **Concepts** are driven by a different algorithm.

### Filtered Review

* **Card Source:**
* Fetches cards into the queue based on filter conditions for review. Normal grading removes the card; clicking **[Rebuild]** re-fetches cards into the queue.
* ![image](https://raw.githubusercontent.com/Dammyxy/siyuan-plugin-siyuanmemo/main/assets/image-20260217151638-cgm7my8.png)

* **Algorithm:** Items/Descriptors use FSRS; Topics/Concepts use a separate algorithm.

## One Static Queue — Deliberate Practice

* **Design Origin:** It should actually be called **Final Drill**, derived from SuperMemo.
* **Card Source:**
1. Cards graded less than 3 in Retrieval Practice, Incremental Learning, or Filtered Review queues automatically drop into **Deliberate Practice**.
2. Manually selecting flashcards in the Browser to add them.


* **Algorithm:**
* Grading does *not* affect the Spaced Repetition scheduling. In this queue, cards are removed only if the grade equals 4. If you keep pressing grade 3, you will never finish the queue.
* The queue sorting uses a local shuffling algorithm. See: [Final drill algorithm](https://supermemopedia.com/wiki/Final_drill_algorithm).



## One Queue Hard to Classify — Neural Roaming

* **Design Origin:** Siyuan's Bidirectional Links and SuperMemo's Neural Review.
* **Card Source:** The object of roaming is the Siyuan Block. This queue automatically fetches the **Backlinks** (Incoming links) of the Concept Card and **Descriptor Cards** for roaming.
* **Algorithm:** **Spreading Activation**.
* **Tip:** During roaming, if you encounter a block reference anchor text, you can Right-click -> **Make as Concept Card and Join Queue**. This way, the **Forward Links** (Outgoing links) of the concept can also join the queue for roaming. The logic is:
* Forward Link = References to other Concepts (Document Blocks) within the main text.
* Backlink = The main text itself.
* Forward Link = References to other concepts found within the Backlinks.
* ![image](https://raw.githubusercontent.com/Dammyxy/siyuan-plugin-siyuanmemo/main/assets/image-20260217163333-r5n304c.png)



# Quick Card Creation

## Symbol Card Creation

* Listens for symbols to quickly create cards. Supports:
* `>>`
* Forward Card
* Question `>>` Answer


* `<<`
* Backward Card
* Answer `<<` Question


* `<>`
* Bidirectional Card
* Term `<>` Definition
* Generates two cards.


* `;;`
* Descriptor Card
* Attribute `;;` Description


* `==Cloze==` or `{{Cloze}}` or Siyuan Mark
* Cloze Card
* Text `{{Cloze}}` or `==Highlight==` or Siyuan Mark (ALT+D)
* Multiple cloze markers will generate multiple cards.


* It will not listen to symbols wrapped in code blocks (``). After typing the symbol, you must press Enter or lose block focus to trigger auto-creation.



## Template Card Creation

Ordered List Templates allow batch card creation sharing the same Block ID. Each card can have individual question supplements or hints.

* **Steps:**
1. **Mandatory Requirement:** The child list block must be an **Ordered List**.
2. **Review Entry:** Right-click the parent list item block.
3. **Create Button:** Select [Plugin] -> [siyuanmemo] -> [Create List Template Card] in the block menu.


* **Writing Supplements/Hints:**
* Hint -> Question
  * Example: In Step 1's `Mandatory Requirement -> The child list block must be an Ordered List`:
  * Symbol -> The text *before* it "Mandatory Requirement" is the **Hint**.
  * Symbol -> The text *after* it "The child list block must be an Ordered List" is the **Question**.




* ## **Demo:**
  - ![PixPin_2026-02-17_17-02-23](https://raw.githubusercontent.com/Dammyxy/siyuan-plugin-siyuanmemo/main/assets/PixPin_2026-02-17_17-02-23-20260217170230-5lnj8ae.gif)

* ## **Review Effect:**
  - ![PixPin_2026-02-17_17-20-40](https://raw.githubusercontent.com/Dammyxy/siyuan-plugin-siyuanmemo/main/assets/PixPin_2026-02-17_17-20-40-20260217172050-aplrjnx.gif)


*Current limitation of Template Creation (Working on it):*

* It doesn't use Siyuan's editor yet, so there is no image display (no image cards) and no LaTeX formula cards.

## CDF Card Creation

* **How to use?**
* Use Transitive Links in the list outline.


1. Type a list block.
2. The Parent Block must reference a Concept Document Block.
3. The Child Block uses `Descriptor;;Text`. Pressing Enter after typing will automatically identify it as a Descriptor Card. If it detects that the referenced Document Block in the parent is not a Concept Card, it will automatically convert it into one.


* **Example:**
* [[Neutron Star]]
  * Definition;; An extremely dense celestial object between a white dwarf and a black hole
  * *Precursor*;; Core remnant of a star with 8-30 solar masses
  * *Intuitive Density*;; One teaspoon weighs 1 billion tons
  * *Special Variant*;; Pulsar
  * *Critical Point*;; Oppenheimer Limit (collapses into a black hole if exceeded)




* ## **Review Effect:**
    - ![PixPin_2026-02-17_18-09-48](https://raw.githubusercontent.com/Dammyxy/siyuan-plugin-siyuanmemo/main/assets/PixPin_2026-02-17_18-09-48-20260217181023-945qx07.gif)

* **Tip:**
* **Deleting Descriptor Cards:**
* For stability reasons, Descriptor cards are created using Paragraph Blocks. If you want to delete a card in the Siyuan Editor, place the cursor in the corresponding block, use `Ctrl+/` to call the block menu, and then "Cancel Flashcard".
* Or simply delete it in the SRS Browser.


* **Create a Template for your common Descriptor combinations!**
1. Focus on your descriptor combination.
2. Click the top-right Document Block icon.
3. Export -> Template.
4. Use `/template` under the corresponding concept to summon the corresponding Descriptor Template.
  - ![image](https://raw.githubusercontent.com/Dammyxy/siyuan-plugin-siyuanmemo/main/assets/image-20260217175020-s0zufqu.png)




# Separation of Blocks and Flashcards (One Block, Multiple Cards)

* Ordinary flashcards are still one block per card. However, **Bidirectional Cards**, **List Template Cards**, and **Multi-Cloze Cards** utilize this separation mechanism.

# Flashcard Planning

## Sort

* You can sort the flashcards in the queue within the Browser. The sorting applies to the queue, changing the order during review.
* Click browser field to sort.
* Right-click -> Sort.
* ## **Demo:**
    - ![PixPin_2026-02-17_18-42-17](https://raw.githubusercontent.com/Dammyxy/siyuan-plugin-siyuanmemo/main/assets/PixPin_2026-02-17_18-42-17-20260217184242-9clerkh.gif)




## Advance

* In the Browser, right-click a card and select **[Advance]**. This corresponds to (is the opposite of) **[Postpone]**.
- ![image](https://raw.githubusercontent.com/Dammyxy/siyuan-plugin-siyuanmemo/main/assets/image-20260217184325-hduqqmx.png)

## Postpone

* In the Browser, right-click a card and select **[Postpone]**.
- ![image](https://raw.githubusercontent.com/Dammyxy/siyuan-plugin-siyuanmemo/main/assets/image-20260217184540-o1c2fwv.png)

## Load Balancing (Spread)

* There is a **[Load Balancing]** button on the Browser toolbar. Clicking it opens the interface.
- ![image](https://raw.githubusercontent.com/Dammyxy/siyuan-plugin-siyuanmemo/main/assets/image-20260217185204-zpfvb1p.png)
* **Note:** The **[Load Balancing]** function under "All Flashcards" has two modes:
1. Process unreviewed cards (Backlog) — default (uncheck "Consider Future Reviews").
2. Process cards scheduled for review in the future (e.g., next year) — select by adjusting the collection period.


* In the Queue View, clicking **[Load Balancing]** defaults to collecting due cards and prevents changing the collection period.