# Using Architectural Zones to Generate Information-Flow-Aware Abstract Penetration Test Cases - ICSA2026
# edu.kit.pentest

A set of Eclipse Modeling / Palladio-based projects for **Using Architectural Zones to Generate Information-Flow-Aware Abstract Penetration Test Cases**.

This repository contains:

- Metamodels for penetration test cases and their extensions
- Generation logic for abstract pen test cases
- A running example from the associated paper
- Evaluation scenarios and models

---

## Projects

### `edu.kit.pentest.evaluation`
The evaluation scenarios and models used to assess the approach.

### `edu.kit.pentest.generation`
Generation logic for penetration test cases based on PCM architectures and the provided extensions.

### `edu.kit.pentest.model`
The core metamodel of the penetration test cases.

### `edu.kit.pentest.runningexample`
The running example from the paper, including:
- Example models in the `models` folder
- `pentestcase.xmi` containing the generated penetration test cases

### `edu.kit.pentest.sidechannel`
The side-channel extension metamodel to the Palladio Component Model (PCM).

### `edu.kit.pentest.sidechannel.generation`
Generation logic for **information flow rules** based on:
- Penetration test cases
- Side-channel extensions

### `edu.kit.pentest.zone`
The zone extension metamodel to PCM.

---

## Prerequisites

- **Eclipse Modeling Tools**  
  Download from the official Eclipse site:  
  https://www.eclipse.org/downloads/  
  > Choose the *Eclipse Modeling Tools* package.
  
- **Palladio Features**  
  Install all Palladio features from the update site:  
  https://updatesite.palladio-simulator.com/palladio-build-updatesite/releases/5.2.1/

---

## Setup

1. **Install Eclipse Modeling Tools**
   - Download and install from: https://www.eclipse.org/downloads/
   - Choose the **Eclipse Modeling Tools** variant.

2. **Install Palladio Features**
   - In Eclipse, go to:  
     `Help` → `Install New Software...`
   - Use the update site:  
     `https://updatesite.palladio-simulator.com/palladio-build-updatesite/releases/5.2.1/`
   - Select and install all Palladio features.

3. **Import the core metamodel projects**
   - Import the following projects into Eclipse:
     - `edu.kit.pentest.model`
     - `edu.kit.pentest.sidechannel`
     - `edu.kit.pentest.zone`

4. **Generate EMF code from the metamodels**
   - For each of the three projects above:
     - Open the corresponding `.genmodel` file.
     - Generate:
       - Model code
       - Edit code
       - Editor code  
       (Alternatively, load all respective generated projects from the replication package, but you may need to adapt project paths.)

5. **Clean the workspace (if needed)**
   - In Eclipse:  
     `Project` → `Clean...` → Clean all projects.

6. **Run an inner Eclipse instance**
   - Launch a second (inner) Eclipse application with the projects installed as plugins:
     - `Run` → `Run Configurations...` → `Eclipse Application` → `Run`

7. **Open the remaining projects in the inner Eclipse**
   - In the **inner Eclipse instance**, import/open:
     - `edu.kit.pentest.generation`  
       → Contains the generation code for abstract pen test cases.
     - `edu.kit.pentest.runningexample`  
       → Contains the running example models in the `models` folder and `pentestcase.xmi` with generated pen test cases.
     - `edu.kit.pentest.evaluation`  
       → Contains evaluation models in the `models` folder and subfolders, plus `pentestcase.xmi` with generated pen test cases.

---

## Re-executing the Penetration Test Case Generation

To re-run the generation logic:

1. In the **inner Eclipse instance**, ensure all relevant projects are open:
   - `edu.kit.pentest.generation`
   - `edu.kit.pentest.runningexample`
   - `edu.kit.pentest.evaluation`

2. Run the following JUnit tests:
   - For the running example:
     - `edu.kit.pentest.runningexample.test.RunningExampleTest`
   - For the evaluation scenarios:
     - `edu.kit.pentest.evaluation.EvaluationTest`
    

3. **Windows-specific note**  
   On Windows, there is a known issue when executing the tests multiple times:
   - You may receive errors about unresolved classes.
   - If this happens:
     - Clean the Eclipse workspace:  
       `Project` → `Clean...`
     - Then run the tests again.

---

## Notes

- If you use the replication package with pre-generated projects, check and adjust any project-specific paths as needed.
- The `models` folders and `pentestcase.xmi` files in the running example and evaluation projects are good starting points to understand the generated penetration test cases.
- Eclipse must be set to use **Java 17** for compiling the project. (should be there by default)
- JUnit5 must be set to use as a testing version. (should be there by default)

## Troubleshooting

### 1) `Test cannot be resolved to a type` / `@Test` is red in Eclipse
**Cause:**
Wrong JUnit import OR JUnit is missing from the build path.

**Fix:**
- make sure JUnit 5 exists in the project build path:
- Project → Properties → Java Build Path → Libraries
- Add JUnit 5

### 2) `Eclipse is running / building with the wrong Java version
**Cause:** 
Eclipse IDE may use one Java version, while the project/compiler uses another.

**Fix(Project build Java version):**
- Window → Preferences → Java → Installed JREs
  - Select the correct JDK (e.g., Java 17) and set it as Default
- Project → Properties → Java Compiler
  - Set the Compiler compliance level to the required version (e.g., 17)
- Restart Eclipse after editing.
