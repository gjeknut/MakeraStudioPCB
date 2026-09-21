# PCB Milling in Makera Studio

This guide covers how to prepare PCB milling toolpaths in Makera Studio. It assumes that the PCB design is already finished and exported from an electronics design tool such as KiCad or EasyEDA.

## Before You Start

Prepare the following files:

- Gerber files for the copper layer(s)
- Drill file(s)
- Board outline file
- A PCB blank with the correct thickness

Before importing, inspect the Gerber files in a Gerber viewer. Make sure tracks, pads, drill holes, and the board outline are correct.

## 1. Create a New Project

1. Open Makera Studio.
2. Create a new CNC project.

<img width="300" height="54" alt="image" src="https://github.com/user-attachments/assets/3e03c608-a197-41e1-a37c-8c42968fce76" />

3. Choose 2D Vector Machining
<table>
  <tr>
    <td>
      <img width="300" alt="Pasted 2026-09-21 at 4 43 23 PM" src="https://github.com/user-attachments/assets/15f552b6-e936-4133-bcd4-e736b0bc1973" />
    </td>
  </tr>
</table>





5. Set PCB as your material and select correct size

<img width="300" alt="Pasted 2026-09-21 at 4 53 11 PM" src="https://github.com/user-attachments/assets/6bf36c4c-81d9-44a6-a684-2171144a71a6" />

7. Set the stock dimensions:
   - Width and height of the PCB blank
   - PCB thickness
8. Choose a work origin that will be easy to locate on the physical PCB blank.

## 2. Import the PCB Design

1. Import the PCB geometry into Makera Studio.
2. Import the copper layer first.
3. Import the drill data and board outline.
4. Check that all imported layers line up correctly.
5. Confirm that the board is facing the correct direction.

> Always check the preview before creating toolpaths. A mirrored design or incorrect layer alignment can ruin the board.

## 3. Create the Isolation Milling Toolpath

Isolation milling removes copper around tracks and pads.

1. Select the copper geometry.
2. Create an engraving, tracing, or isolation toolpath.
3. Choose a V-bit or PCB engraving bit.
4. Set a shallow cutting depth.
5. Select the areas where copper should be removed.
6. Generate the toolpath.
7. Use the simulation to confirm that tracks and pads remain intact.

A shallow cut is important. Cutting too deep makes tracks wider and reduces tool life.

## 4. Create the Drilling Toolpath

1. Select the drill-hole geometry.
2. Create a drilling toolpath.
3. Choose the correct drill diameter.
4. Confirm the hole positions in the preview.
5. Generate the toolpath.

If the design uses multiple drill sizes, create separate drilling operations for each size.

## 5. Create the Board Outline Toolpath

The outline toolpath cuts the PCB free from the blank.

1. Select the board outline.
2. Create a contour or profile toolpath.
3. Choose a small end mill.
4. Set the final cutting depth slightly deeper than the PCB thickness.
5. Add tabs if required to keep the PCB in place.
6. Generate the toolpath.

The outline operation should always be last.

## 6. Check Operation Order

Use this order:

1. Isolation milling
2. Drilling
3. Board outline

This keeps the PCB stable until all tracks and holes have been completed.

## 7. Simulate the Complete Job

Before sending the job to the machine, run the simulation and verify:

- All tracks are isolated correctly
- Pads remain connected to their tracks
- Drill holes are in the correct locations
- The board outline matches the design
- The cutting depth is appropriate
- Operations run in the correct order
- No unwanted areas are machined

## 8. Export or Send the Job

When the simulation looks correct:

1. Save the Makera Studio project.
2. Send or export the job for your Makera machine.
3. Keep the project file, Gerber files, and tool list together for future revisions.

## Common Problems

| Problem | Possible Cause | Solution |
| --- | --- | --- |
| Tracks are too wide | Isolation cut is too deep | Reduce the cutting depth |
| Copper remains between tracks | Cut is too shallow | Increase the cutting depth slightly |
| Holes are misplaced | Drill data is misaligned | Check import alignment and work origin |
| Board outline is wrong | Incorrect contour selected | Verify the imported outline geometry |
| PCB moves during cutting | Outline is cut too early | Keep contour cutting as the final operation |

## Recommended First Test

Before milling a real circuit, make a small test pattern containing:

- Tracks with different widths
- Pads with different spacing
- Several drill-hole sizes
- A simple board outline

Use the result to find the isolation depth and tool combination that works best for your PCB material.
