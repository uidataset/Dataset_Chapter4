# **Eleva**

> Official repo for Eleva dataset

Eleva, a highly targeted dataset that contains 10 applications and 3,182 classes of UI elements, with a total of 32,807 samples distributed across these classes. These samples span diverse UI variations across multiple devices, app-specific and display modes, and have been carefully filtered to include challenging cases that existing static rules cannot fully cover.

## Dataset Structure

The dataset consists of 10 applications, each containing multiple workflows. Each workflow will be executed on different devices and modes, ensuring that corresponding pages from multiple samples of the same workflow can be directly aligned.

The root directory contains the following:

- `data/` - A directory containing subdirectories for each specific app's workflows
- `dataDescription.xlsx` - An Excel file used to summarize the information about the data.

### `data` Directory

The structure of each workflow under each application is as follows:

- application

  - workflow

    - **_labels** 

      Contains the labeled UI element information for each page in the current workflow, in the form of **label_{idx},json**, where `idx` is the page index in the workflow.

      - label_0.json
      - label_1.json
      - ···
      - label_X.json

    - Execution Device / Mode 1 

      Contains images of the pages in the workflow and the UI tree information corresponding to each page.

      - screen_infos: Image of each page
      - layout_infos: Accessibility node tree of each page
      - shortcut_data.json: Workflow operation log

    - Execution Device / Mode 2

    - ···

    - Execution Device / Mode X

#### label_{idx}.json

1. The labeled UI element information for each page is a two-dimensional matrix.
   - [
     - [All variants of Element1]
     - [All variants of Element2]
     - xxx
     - [All variants of ElementX]
   - ]
2. For each specific UI element, the following attributes are recorded:
   - bounds: The bounding box of the UI element on the current page
   - img_path: The image path of the page corresponding to the UI element
   - semantic: The semantic label of the UI element
3. It is important to note that the number of `label_{idx}.json` files may **not be the same as** the number of pages in the current workflow. This is because in the same application, different workflows may share some common pages. In this case, the labeled UI element information for the same page will only be recorded in the **_labels** of **one** workflow.

## **License**

This work is licensed under a [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/).

