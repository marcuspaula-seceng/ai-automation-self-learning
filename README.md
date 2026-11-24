# AI Automation & Self-Learning

A public project for building a self-directed learning workflow with an AI tutor, a second brain for study notes, and practice that tests what the learner can do independently.

## Start the pilot

Open the [seven-day pilot](pilot/one-week.md) and take the baseline check on Day 1. Use the [second-brain note template](templates/study-note.md) to capture what you learn and the [AI tutor prompt](prompts/ai-tutor.md) to practice.

## Try the workflow

1. **Set an outcome.** Pick one skill and write down what you want to be able to explain or do. For example, write a spreadsheet formula that sums values by category.
2. **Capture a source.** Save the source link, your explanation in your own words, one worked example, and a question you still have.
3. **Practice with an AI tutor.** Attempt the exercise first. Ask for one hint at a time and check factual claims against the source.
4. **Review from memory.** Answer three questions before opening the note. Record what you remembered, correct one gap, and set the next review date.

Try this tutor prompt with a public or fictional source:

> Ask me one question about this topic at a time. Wait for my attempt, then give one hint if I need it. Let me revise my answer before explaining the solution. Point out any claim I should verify against the source.

## Draft and approve a study note

The [command-line automation](automation/study_note.py) takes a UTF-8 text or Markdown source and drafts an English study note with a summary, a worked example, and exactly three review questions with answers. It uses Python 3.10 or newer and a running local Ollama instance with a downloaded model. The script requires no Python packages. See [Ollama's structured output documentation](https://docs.ollama.com/capabilities/structured-outputs).

1. Run the draft command from the repository root. Replace `YOUR_LOCAL_MODEL` with the name of a locally installed model. The example uses [fictional spreadsheet data](examples/conditional-sums.txt). Choose a new draft path outside the public checkout and the second-brain folder.

   ```text
   python automation/study_note.py draft examples/conditional-sums.txt --model YOUR_LOCAL_MODEL --output ../conditional-sums-draft.json
   ```

2. Inspect the draft against the source. Add `--reference` when drafting to preserve a source URL or a stable identifier instead of the default file name. The draft includes this reference and a SHA-256 fingerprint of the normalized source text.
3. Preview the Markdown output with the approval command. Use an existing folder for your second brain.

   ```text
   python automation/study_note.py approve ../conditional-sums-draft.json --vault ../second-brain
   ```

4. Type `APPROVE` only when satisfied with the exact preview. Any other reply keeps the draft without saving a note. Approving the same source again in the same folder leaves the existing note intact. The JSON draft is retained after approval.

The script sends the source to the Ollama API at `127.0.0.1:11434`. Select a local model. Keep your source files, drafts, and approved notes in your own storage.

## First milestone

Run the workflow for one week on a single topic. Compare a short recall check before and after the pilot, and use the result to choose one improvement. The draft-and-approve automation supports the Day 6 review exercise.

| Order | Task |
| --- | --- |
| 1 | [Define a one-week learning pilot](../../issues/1) |
| 2 | [Create a second-brain note template](../../issues/2) |
| 3 | [Build an AI tutor prompt for practice](../../issues/3) |
| 4 | [Prototype a source-to-study-note automation](../../issues/4) |
| 5 | [Run a weekly recall and review](../../issues/5) |

## Public contributions

Use generic or fictional study records in examples and issues. Keep personal notes, private source material, and credentials in your own storage. This repository contains the pilot materials, the study-note automation, and the initial backlog.
