## Zotero Obsidian Workflow

This workflow can allow you to import your Zotero annotation into Obsidian to facilitate the organization of your reading.

### Step 1
- Install the `Obsidian Zotero Integration` plugin into your Obsidian vault
    - You can follow the instruction to do so [here!](https://github.com/mgmeyers/obsidian-zotero-integration)
- Add the content of `font.css` into your Obsidian's snippets CSS file
- Use `note-template.md` as a template for your `Obsidian Zotero Integration` plugin

### Step 2
- Read your paper in Zotero
- Leverage Zotero color's system to define your note-taking strategy
- Here is the strategy I use for the current workflow (you can adapt the template to your own need!):
    - I use all 5 colors for highlighting:
        - Yellow is used for the contributions of the paper
        - Blue is used for the results of the study
        - Purple serves two purposes:
            - Motivations of the paper, implementation details, or general comment
            - Highlight parts of the paper that are interesting from a writing perspective (e.g., how results are presented). Such highlights are tagged with the "#writing_inspiration" hashtag
        - Green is used for highlighting connected literature I should read
        - Red is used for highlighting limitations and assumptions made in the paper.
    - Additionally, I take personal notes (no color rule is applied here). Notes related to the writing/organizational aspect of the paper are also tagged with the "#writing_inspiration" hashtag

### Step 3
- Once the reading is done, import your annotations into your Obsidian vault
- The imported note is organized as follows:
    - A header containing metadata of the paper (title, authors, citekey) and tags
    - An empty "Research note" section. 
        - Placing your distilled notes between "%% begin notes %%" and "%% end notes %%" ensure that your research note are not overwritten
    - An "Annotation" section containing the different annotations
    - Each annotation contains a checkbox that can be checked once the annotation is processed into a distilled note
    - Annotations are persistent. That is, only the annotations that were not added since the last import are added when the import is done on the same paper.
    
