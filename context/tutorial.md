# Tutorial Workflow and Guidelines

This document extracts the tutorial-specific parts for developing workshop tutorials. It outlines the step-by-step flow for creating a tutorial, the project-specific structure, and the detailed development guidelines.

## Project Structure

- `workshop/`: Contains markdown tutorial files.
- `solution/`: Contains reference implementations for each tutorial.
- `poc/`: Contains temporary proof-of-concept implementations while creating the tutorial.
- `src/`: Serves as the starting point for workshop participants.

## Pre-tutorial Setup

The following files must be created to bootstrap any tutorial project:

- `README.md`: Root-level setup guide that matches the first tutorial (01-workshop-setup)
- `src/verify.py`: Verification script to confirm environment setup
- `src/requirements.txt`: Project dependencies
- `workshop/01-workshop-setup.md`: Initial tutorial containing setup instructions

These files ensure participants can properly configure their environment before starting the workshop. The README.md and first tutorial should be identical to maintain consistency. It will guide participants in installing the required software and setting up the virtual environment, and run the verification script to confirm it works.

## Specific Tutorial Flow
1. **Create a Tutorial Step**
   - Create a new tutorial step instructions (e.g., `workshop/08-improved-ui.md`).
2. **Implement a Proof-of-Concept (POC) Folder**
   - Copy the solution from the previous step (e.g., step `solution/07-*`) into the `poc/` folder.
   - Follow the new tutorial step instructions to implement the POC.
3. **Iterate Until Working Code**
   - Refine the copy iteratively until the code functions as expected.
4. **Update the Tutorial**
   - Update the tutorial step instructions to align with the working code in the POC.
   - Ensure each tutorial step is documented step-by-step and that the instructions are clear.
5. **Implement the Final Solution**
   - Integrate the final, polished solution into the `solution/` folder for reference.

## Workshop Progression

- Tutorials build incrementally on previous knowledge.
- After completing each tutorial, participants should have code similar to the corresponding `solution/` folder.
- Example: After tutorial 01, the code should match `solution/01-*`, which then serves as the base for tutorial 02.

## Tutorial Development Guidelines

### Core Principles for Tutorial Building

1. **Minimal, Testable Changes**
   - Start with the absolute minimum change that can be tested
   - Each modification must be independently verifiable
   - NEVER combine multiple concepts in one step
   - Participants should have working code at every point

2. **Building on Previous Code**
   - Each section starts with what participants already have (working code)
   - NEVER overwrite code blocks from previous sections
   - Always create new sections to expand functionality
   - Show exactly which previous code is being modified

3. **Step Organization Example**
   Adding function calling to a chatbot:
   ```
   Step 08: Function Calling
   
   Section 01. Basic Tool Registry
   - Add tools/ folder with calculator.py
   - Create registry.py with basic registration
   - Add __main__ test in calculator.py
   - Verify: Run calculator.py to test registration
   
   Section 02. LLM Integration
   - Add method to fetch registered tools
   - Update LLM with tool knowledge
   - Verify: LLM knows about calculator
   
   Section 03. Function Calling
   - Add function call prompting
   - Verify: LLM can use calculator
   
   Section 04. Tool Discovery
   - Add endpoint to expose tools
   - Update UI to show available tools
   - Verify: Tools visible in UI
   ```

4. **Code Evolution Format**
   ```markdown
   In `app.py`, find this code from section 01:
   ```python
   def register_tool(name, tool):
       tools[name] = tool
   ```
   
   Update it to handle tool state:
   ```python
   def register_tool(name, tool):
       tools[name] = {
           'implementation': tool,
           'enabled': True
       }
   ```
   ```

5. **Verification Requirements**
   - Every code change must have clear verification steps
   - Show exact commands to run
   - Describe what success looks like
   - Include common error cases and solutions

6. **POC Development Process**
   - Develop each step in poc/ folder first
   - Test minimal changes independently
   - Document in tutorial only after verification
   - Create new sections for changes instead of modifying previous ones

7. **Tutorial Writing Flow**
   - Start each section by stating what participants have
   - Clearly identify the new feature being added
   - Show minimal changes for that single feature
   - Include verification steps
   - Move to next section for next feature
