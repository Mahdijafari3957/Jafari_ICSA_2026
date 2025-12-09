# Zonning_ICSA_2026
Projects
edu.kit.pentest.evaluation
The evaluation scenarios.
edu.kit.pentest.generation
The generation of pen test cases based on architectures and extensions.
edu.kit.pentest.model
The metamodel of the pen test cases.
edu.kit.pentest.runningexample
The running example from the paper.
edu.kit.pentest.sidechannel
The side channel extension metamodel to PCM.
edu.kit.pentest.sidechannel.generation
The generation logic for information flow rules based on the pen test cases and the side channel extensions.
edu.kit.pentest.zone
The zone extension metamodel to PCM.
Setup
·	Install Eclipse Modeling Tools from https://www.eclipse.org/downloads/
·	Chose the Eclipse Modeling Tools variant
·	Install all Palladio Features from updatesite https://updatesite.palladio-simulator.com/palladio-build-updatesite/releases/5.2.1/ through Install New Features into eclipse
·	Open the projects edu.kit.pentest.model, edu.kit.pentest.sidechannel, edu.kit.pentest.zone in eclipse
·	Open the .genmodel files for all three projects, generate the model code, the edit code, and the editor code (or load all the respective projects from the replication package, which might need additional modifications in regard to paths)
·	If necessary, clean the workspace through Project - Clean
·	Run an inner eclipse instance with the projects opened installed as plugins
·	In the inner instance, open the project edu.kit.pentest.generation to view the code for the generation of the abstract pen test cases
·	In the inner instance, open the project edu.kit.pentest.runningexample to view the models of the running example in the models folder or also the pentestcase.xmi to view the generated pen test cases
·	In the inner instance, open the project edu.kit.pentest.evaluation to view the models of the evaluation in the models folder and the respective subfolder or also the pentestcase.xmi files to view the generated pen test cases
·	To re-execute the penetration test case generation, run the edu.kit.pentest.runningexample.test.RunningExampleTest or edu.kit.pentest.evaluation.EvaluationTest (on Windows, we have an unknown bug which prevents us from executing the tests multiple times without cleaning eclipse, so if you get errors about unresolved classes, please clean your eclipse workspace once and try to run the tests again)
