# Task A: Generation Quality Assessment Tool

## Overview
This tool is designed to facilitate the **human evaluation** component of the Abstract Visual Reasoning Benchmark. Evaluators will assess AI-generated images based on their semantic alignment with abstract concepts (such as Idioms, Film & TV, and Literary Works).

The tool runs entirely in your web browser. It automatically samples the required **100 test images** (Seed 42) from your source dataset and exports a standardized CSV file for analysis.

---

## 🚀 Getting Started

1.  **Download** the file `TaskA_Quality_Assessment.htm` to your local machine.
2.  **Open** the file in a modern web browser (Chrome, Edge, Firefox, or Safari).
3.  No internet connection is required after the page loads; the tool runs locally.

---

## 🖥️ Workflow Guide

### Step 1: Annotator Login
Upon opening the tool, you will be greeted by the landing page.
* **Action:** Enter your Name or Annotator ID.
* **Purpose:** This name will be appended to your final results file (e.g., `Task_A_Scores(Alex).csv`) to track contributions.

<img width="917" height="554" alt="image" src="https://github.com/user-attachments/assets/a7de5c07-34ac-4e14-ac70-d351387e748a" />

---

### Step 2: Training Module
Before starting, you must review the evaluation criteria. The tool includes an interactive guide covering all 6 domains (Literary Works, Film & TV, Public Figures, Idioms, Fictional Characters, Places).

* **Navigation:** Use the **"Next Section →"** button to read through the specific rubrics and case studies for each domain.
* **Completion:** Once you reach the final section, click **"Understood! Let's Go!"** to proceed.


<img width="1666" height="901" alt="image" src="https://github.com/user-attachments/assets/7d18f5fe-b5c8-42ca-8eb8-f58fa729b957" />
<img width="1659" height="897" alt="image" src="https://github.com/user-attachments/assets/f835e973-dedd-41aa-ad6f-cbdb78c86e04" />

---

### Step 3: Data Setup
You will be prompted to load the image dataset.
* **Action:** Click **"📂 Load Image Folder"**.
* **Selection:** Select the folder on your computer that contains the full set of source images (300+ images).
* **Auto-Sampling:** The tool will automatically sort the files and select the specific **100 images** required for this evaluation task.

<img width="805" height="413" alt="image" src="https://github.com/user-attachments/assets/9f7a842a-9d0b-4f9c-8c29-5e29042ad29b" />

---

### Step 4: Annotation Interface
This is the main workspace. You will view images one by one and assign a quality score (1-5).

<img width="1806" height="980" alt="image" src="https://github.com/user-attachments/assets/b2256053-acd4-4335-b178-a75fa0236c8d" />


#### 🎮 Controls & Buttons

<table>
  <thead>
    <tr>
      <th width="18%">Button / Area</th>
      <th>Function</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Score Buttons (1-5)</b></td>
      <td>Assigns a score to the current image. Clicking a score automatically advances to the next image after a short delay. You can also use keyboard keys <code>1</code> through <code>5</code>.</td>
    </tr>
    <tr>
      <td><b>← Previous / Next →</b></td>
      <td>Manually navigate through the image list without changing scores.</td>
    </tr>
    <tr>
      <td><b>📖 Go Back to Guide</b></td>
      <td>Opens the Training Module overlay. Use this if you need to double-check the rubric for a specific domain while working.</td>
    </tr>
    <tr>
      <td><b>💾 Save CSV</b></td>
      <td>Exports your progress to a <code>.csv</code> file. <b>Save frequently.</b></td>
    </tr>
    <tr>
      <td><b>🗑️ Reset</b></td>
      <td>Clears all current scores. Use with caution.</td>
    </tr>
    <tr>
      <td><b>Thumbnail Grid</b><br><em>(Left Panel)</em></td>
      <td>Shows your progress. Images with a green checkmark (<code>✓</code>) have been scored. Click any thumbnail to jump to that image.</td>
    </tr>
  </tbody>
</table>

---

## 📊 Scoring Rubric Summary

The tool uses a **1-5 Scale** to measure Semantic Alignment:

* **1 - Literal Assemblage:** A collage of objects with no thematic logic.
* **2 - Vague/Iconic:** Shows the subject but lacks specificity or emotion.
* **3 - Emotion w/o Context:** Captures the internal feeling but misses the triggering situation.
* **4 - Contextual Narrative:** Visualizes a scenario that naturally evokes the concept.
* **5 - Artistic Mastery:** Professional quality; seamless integration of style, context, and meaning.

---

## 📂 Output

When you click **Save CSV**, the tool generates a file named:
`Task_A_Scores(YourName).csv`

**Format:**
```csv
image_filename,quality_score
interstellar_01.jpg,4
newton_03.jpg,2
...
