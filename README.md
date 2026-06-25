# Quantum Software Testing

---

This repository contains experiments conducted in the paper *“Professionals’ Expectations on Quantum Software Testing: A Large-Scale Empirical Study.”*

## Abstract
Quantum Software Testing (QST) has attracted increasing attention as quantum systems 
grow in complexity and quantum development practices continue to evolve.
Recent studies in QST have proposed various techniques
to assess and test the reliability of quantum systems, and have
shown promising effectiveness. However, the performance of
QST in practice is tightly coupled and constrained by various
factors (e.g., information availability, the properties of execution
backends). It is therefore of high importance to examine whether
these QST tools have (1) met the demands faced by the quantum
computing community and (2) aligned with the current practice
of quantum system development.
To answer these, this paper presents the first large-scale empirical study in QST, composed of two stages: (1) a mixed-methods
study, containing qualitative interviews with 8 professionals in
quantum computing and quantitative forum analysis on 2,740
discussion posts, and (2) a literature review of 62 QST papers
to analyze whether the proposed tools address the identified
challenges from the first stage.

## Repository Strcutrue

---

```text
EmpiricalStudy/
├── interview-study/
│   ├── interview_guide.pdf
│   ├── participant_information.pdf
│   └── README.md

├── forum-analysis/
│   ├── 622_subtopic_labeled_posts.xlsx
│   ├── 2740_concept_labeled_posts.xlsx
│   ├── subtopic_definition.txt
│   └── README.md 
│
├── literature-review/
│   ├── selected_papers.xlsx
│   ├── keywords.pdf
│   └── README.md 
│
└── README.md

```
This paper presents a two-stage large-scale empirical study: stage 1 contains a mixed-methods study, 
with qualitative interview study and quantitative forum analysis. 
Stage 2 contains a literature review of 62 papers in a challenge-driven, 
practice-oriented perspective.
* `interview-study/`: Materials related to the professional interviews (RQ1).
* `forum-analysis/`: Materials related to the forum analysis (RQ2).
* `literature-review/`: Materials related to the literature review (RQ4). RQ3 contains finding triangulation and challenge identification.


## Sample Posts (Forum Analysis)

---

### Representative Posts for QST Subtopics

The following table provides one representative forum post for each QST subtopic (24 subtopics in total). Each example illustrates the primary issue captured by the corresponding subtopic.
<table>
<thead>
<tr>
<th align="center" width="7%"><small>Main Topic</small></th>
<th align="center" width="18%"><small>Subtopic</small></th>
<th align="left" width="58%"><small>Representative Post</small></th>
</tr>
</thead>
<tbody>

<tr>
<td rowspan="2"><small><strong>T1</strong></small></td>
<td><small>T1.1. Correctness checking using available reference information, such as expected outputs or statevectors.</small></td>
<td><small><strong>Question:</strong> For a given unitary <code>U = exp(−itH)</code>, I can use the statevector in a simulator to check whether it evolves correctly. ... How can I check its correctness on a real quantum computer?<br><br>
<strong>Accepted answer:</strong> Perfectly correct evolution cannot be obtained on current noisy hardware. ... First verify the circuit on an ideal simulator, and then compare the hardware result with the simulated result.</small></td>
</tr>

<tr>
<td><small>T1.2. Correctness checking without efficient classical simulation.</small></td>
<td><small><strong>Question:</strong> Is there a practical benchmark that allows a classical verifier to validate a near-term quantum computer without efficient classical simulation or extrapolation? ... Existing benchmarks still require classical verification of output probabilities.<br><br>
<strong>Accepted answer:</strong> A computational Bell test can let a classical verifier check a quantum prover using secret prime factors. ... Reliably passing indicates that the prover either factored the challenge or maintained the required quantum superposition.</small></td>
</tr>

<tr>
<td rowspan="3"><small><strong>T2</strong></small></td>
<td><small>T2.1. Localization of faulty gates, qubits, stabilizers, decoders, or logical operations.</small></td>
<td><small><strong>Question:</strong> When decoding noisy syndromes, failed cases produce predicted logical flips that are the logical NOT of the actual flips. ... Why does this occur?<br><br>
<strong>Accepted answer:</strong> If the data qubits are not all <code>0</code> or all <code>1</code>, detection events remain. ... The decoder removes all detection events and forces the system into either the all-<code>0</code> or all-<code>1</code> state.</small></td>
</tr>

<tr>
<td><small>T2.2. Faults caused by interactions among gates, qubits, errors, or execution stages.</small></td>
<td><small><strong>Question:</strong> A phase flip changes the state but not its computational-basis probabilities. ... What effect does it have during computation?<br><br>
<strong>Accepted answer:</strong> The phase flip matters when the state interacts with later gates. ... A <code>Z</code> error between two <code>H</code> gates changes the final state and measurement probabilities.</small></td>
</tr>

<tr>
<td><small>T2.3. Propagation of physical or logical errors through gates and circuits.</small></td>
<td><small><strong>Question:</strong> A decoder identifies where a Pauli error occurred. ... How should its effect be propagated through the circuit?<br><br>
<strong>Accepted answer:</strong> Propagating every decoded error separately is costly. ... Instead, precompute which logical observables are flipped by each Pauli error.</small></td>
</tr>

<tr>
<td rowspan="3"><small><strong>T3</strong></small></td>
<td><small>T3.1. Requirements and difficulties in preparing a required quantum state.</small></td>
<td><small><strong>Question:</strong> Quantum algorithms require specified input states, but measurement outcomes are random. ... Can I force qubits into a required state?<br><br>
<strong>Accepted answer:</strong> Quantum computers typically start in |0⟩<sup>⊗n</sup>. ... Prepare |ψ⟩ using a unitary <code>U</code> satisfying <code>U|0⟩<sup>⊗n</sup> = |ψ⟩</code>.</small></td>
</tr>

<tr>
<td><small>T3.2. Input validity and algorithm-specific input requirements.</small></td>
<td><small><strong>Question:</strong> Will quantum counting work with a nonuniform superposition over only some basis states? ... Can this state be used as the input?<br><br>
<strong>Accepted answer:</strong> The input can be a uniform superposition over a selected subset. ... The diffusion operator must be changed to <code>2|φ⟩⟨φ| − I</code>.</small></td>
</tr>

<tr>
<td><small>T3.3. Construction of valid quantum oracles and problem instances.</small></td>
<td><small><strong>Question:</strong> Does Grover's oracle require a new ancilla in every iteration because the ancilla becomes entangled? ... Would this cause exponential memory usage?<br><br>
<strong>Accepted answer:</strong> The ancilla remains unentangled and can be reused. ... Phase kickback reverses the phases of marked states while leaving the ancilla unchanged.</small></td>
</tr>

<!-- ==================== T4 ==================== -->

<tr>
<td rowspan="10"><small><strong>T4</strong></small></td>
<td><small>T4.1. General physical noise and errors in quantum hardware.</small></td>
<td><small><strong>Question:</strong> I want to model a time-dependent dephasing channel whose error magnitude grows with <code>t</code>. ... How can I represent dephasing variance proportional to <code>t²</code> rather than <code>t</code>?<br><br>
<strong>Accepted answer:</strong> Such time-dependent noise channels can be obtained from the Lindblad differential equation. ... Integrating it over a duration <code>t</code> gives the corresponding quantum channel.</small></td>
</tr>

<tr>
<td><small>T4.2. Transpilation and logical-to-physical qubit mapping.</small></td>
<td><small><strong>Question:</strong> I have a circuit defined in pytket, Qiskit, or another SDK. ... How can I compile it into the native gate set of a Quantinuum trapped-ion device or emulator?<br><br>
<strong>Accepted answer:</strong> Use the <code>pytket-quantinuum</code> extension and compile the circuit through a <code>QuantinuumBackend</code>. ... For H1-1, the compiled circuit uses native gates such as <code>{Rz, PhasedX, ZZPhase}</code>.</small></td>
</tr>

<tr>
<td><small>T4.3. Differences in physical qubit or gate quality.</small></td>
<td><small><strong>Question:</strong> Qudits represent the same state space with fewer physical units than qubits. ... Why are they less widely used, and what practical values of <code>d &gt; 2</code> might be feasible?<br><br>
<strong>Accepted answer:</strong> Qudits require substantially more calibration, especially for additional transitions and multi-qudit gates. ... Higher levels also tend to have shorter coherence times, so it is unclear whether the larger Hilbert space justifies the added complexity.</small></td>
</tr>

<tr>
<td><small>T4.4. Constraints arising from particular physical platforms.</small></td>
<td><small><strong>Question:</strong> I tested a program on IBM superconducting hardware and now want to compare it with trapped-ion devices. ... Which platform differences should I examine?<br><br>
<strong>Accepted answer:</strong> Trapped-ion systems can provide nearly all-to-all connectivity, whereas superconducting devices have restricted coupling topologies. ... Superconducting implementations may therefore require additional SWAP gates, reducing overall fidelity.</small></td>
</tr>

<tr>
<td><small>T4.5. Execution cost, access, queues, quotas, and operational overhead.</small></td>
<td><small><strong>Question:</strong> A simple Bell-state circuit on <code>ibm_canberra</code> used 24 seconds of runtime, costing about \$40. ... Why does such a small circuit take so long?<br><br>
<strong>Accepted answer:</strong> Real-device execution includes overhead such as job submission, waveform generation, and qubit resets. ... Qubit operations are also slower than classical operations, while quantum speedups generally appear only for sufficiently large problems.</small></td>
</tr>

<tr>
<td><small>T4.6. Error-mitigation methods, behavior, and limitations.</small></td>
<td><small><strong>Question:</strong> With two shots, I expected either a 100% outcome or a 50/50 distribution, but the Sampler returned <code>{0: 0.459, 1: 0.541}</code>. ... Is this caused by error mitigation?<br><br>
<strong>Accepted answer:</strong> Yes, the Sampler applies readout-error mitigation by default. ... It therefore returns quasi-probabilities, which can even fall outside <code>[0, 1]</code>; the mitigation settings can be changed or the Estimator can be used instead.</small></td>
</tr>

<tr>
<td><small>T4.7. Limitations caused by relaxation, dephasing, and finite coherence time.</small></td>
<td><small><strong>Question:</strong> IBM hardware properties list <code>T₁</code>, <code>T₂</code>, readout errors, and gate times. ... What do <code>T₁</code> and <code>T₂</code> represent?<br><br>
<strong>Accepted answer:</strong> <code>T₁</code> measures how quickly |1⟩ relaxes to |0⟩, while <code>T₂</code> measures how quickly a coherent superposition loses its relative phase. ... Operations longer than <code>T₂</code> can make intermediate measurements impractical.</small></td>
</tr>

<tr>
<td><small>T4.8. Quantum error correction, syndrome decoding, and logical reliability.</small></td>
<td><small><strong>Question:</strong> MWPM selects the most probable individual error, whereas maximum-likelihood decoding selects the most probable stabilizer-equivalent coset. ... Can MWPM choose a correction outside the most probable coset?<br><br>
<strong>Accepted answer:</strong> A unique correction of weight 12 may compete with many equivalent corrections of weight 13. ... MWPM selects the weight-12 correction, while maximum-likelihood decoding selects the weight-13 coset when its combined probability is higher.</small></td>
</tr>

<tr>
<td><small>T4.9. Fault-tolerant computation and threshold guarantees.</small></td>
<td><small><strong>Question:</strong> Is there a proof that measurement-based quantum computation remains fault tolerant under arbitrary noise? ... Does such a result hold for sufficiently short noise-correlation lengths?<br><br>
<strong>Accepted answer:</strong> Nielsen and Dawson studied fault-tolerant measurement-based computation using cluster states. ... They proved threshold theorems analogous to those for the quantum circuit model.</small></td>
</tr>

<tr>
<td><small>T4.Others. Other hardware-, noise-, QEC-, or fault-tolerance-induced constraints.</small></td>
<td><small><strong>Question:</strong> Can a physical qubit represent a measurement probability with extremely high precision, such as 100 decimal places? ... Do hardware qubits impose a precision limit?<br><br>
<strong>Accepted answer:</strong> Quantum mechanics imposes no limit on the precision of θ in <code>cos(θ)|0⟩ + sin(θ)|1⟩</code>. ... Current hardware cannot prepare such states with arbitrary fidelity, and greater logical precision would require more physical qubits for error correction.</small></td>
</tr>

<!-- ==================== T5 ==================== -->

<tr>
<td rowspan="6"><small><strong>T5</strong></small></td>
<td><small>T5.1. Simulation infeasibility caused by memory, qubit count, or state-space growth.</small></td>
<td><small><strong>Question:</strong> Memory limitations stop my Clifford+<code>T</code> circuit simulation at <code>n = 16</code> qubits. ... Is there a method or library that would let me simulate up to <code>n = 40</code> qubits?<br><br>
<strong>Accepted answer:</strong> Universal simulation is limited in qubit count, while specialized Clifford+<code>T</code>, extended-stabilizer, and matrix-product-state simulators can support larger systems. ... Real hardware is another option, although decoherence may obscure the results.</small></td>
</tr>

<tr>
<td><small>T5.2. Differences in how simulators and hardware execute operations.</small></td>
<td><small><strong>Question:</strong> I want to project a qubit to |0⟩ in the middle of a Qiskit circuit. ... Can this operation work on real hardware?<br><br>
<strong>Accepted answer:</strong> IBM hardware provides a <code>reset</code> operation that returns a selected qubit to |0⟩ during circuit execution. ... The same operation is available in the circuit composer.</small></td>
</tr>

<tr>
<td><small>T5.3. Incomplete, inaccurate, or unsupported simulator noise models.</small></td>
<td><small><strong>Question:</strong> I want to model leakage in Stim, including leakage that persists until reset, spreads through CZ gates, or later decays. ... Can Stim simulate these time-correlated effects?<br><br>
<strong>Accepted answer:</strong> Stim’s circuit format does not directly support time-correlated leakage errors. ... You must track leaked qubits yourself with the tableau simulator, including their spread, decay, and removal by reset.</small></td>
</tr>

<tr>
<td><small>T5.4. Differences between simulator and real-hardware results.</small></td>
<td><small><strong>Question:</strong> My two- and three-qubit Grover circuits work reasonably well, but the four-qubit version succeeds only about 10\% of the time on <code>ibmq_quito</code>, despite working in simulation. ... Why?<br><br>
<strong>Accepted answer:</strong> Transpilation for the device’s connectivity expands the circuit to about 196 gates, including roughly 50 CNOTs. ... Given the gate and readout errors, the hardware execution has a high probability of failure.</small></td>
</tr>

<tr>
<td><small>T5.5. Computational or memory overhead in classical simulation.</small></td>
<td><small><strong>Question:</strong> I estimated that an n-qubit density matrix requires <code>4ⁿ + 2ⁿ/2 − 1</code> independent real parameters, while Nielsen and Chuang state <code>4ⁿ − 1</code>. ... Which is correct?<br><br>
<strong>Accepted answer:</strong> Nielsen and Chuang are correct: diagonal entries are real, while each independent off-diagonal complex entry requires two real numbers. ... Including the trace-one constraint gives <code>4ⁿ − 1</code> parameters.</small></td>
</tr>

<tr>
<td><small>T5.6. Simulator-supported operations or information unavailable on hardware.</small></td>
<td><small><strong>Question:</strong> Why must I measure a circuit before running it on real hardware, while a statevector simulator does not require measurement? ... Can hardware return the statevector directly?<br><br>
<strong>Accepted answer:</strong> A real quantum computer cannot directly expose its statevector. ... Information must be obtained by measurement, which collapses the qubits to basis outcomes such as |0⟩ or |1⟩.</small></td>
</tr>

</tbody>
</table>

### Representative Posts for Forum Concepts

We classify the collected forum posts into four concepts according to the primary purpose of each discussion. The following table provides one representative post for each concept and reports its frequency in the dataset.

<table>
<thead><tr>
<th align="left" width="12%"><small>Concept</small></th>
<th align="left" width="45%"><small>Description</small></th>
<th align="left" width="38%"><small>Representative Post</small></th>
<th align="right" width="9%"><small>Posts</small></th>
</tr>
</thead>
<tbody>
<tr>
<td><small><strong>Theoretical</strong></small></td>
<td><small>Discussions primarily concerned with quantum-computing theories, principles, algorithms, mathematical formulations, or conceptual reasoning.</small></td>
<td><small><em>State tomography with Pauli-basis measurements for a large number of qubits.</em></small></td>
<td align="right"><small><strong>1,906</strong><br>69.6%</small></td>
</tr>
<tr>
<td><small><strong>Practice</strong></small></td>
<td><small>Discussions about practical quantum-computing activities, including hardware characteristics, backend behavior, circuit execution, device calibration, and platform-specific observations.</small></td>
<td><small><em>CNOT error rate of 1 on IBM backends: Some CNOT gates display an error rate of 1, whereas typical error rates are much lower. How is that possible?</em></small></td>
<td align="right"><small><strong>644</strong><br>23.5%</small></td>
</tr>
<tr>
<td><small><strong>Learning</strong></small></td>
<td><small>Discussions requesting learning resources, references, tutorials, existing techniques, or general guidance for understanding and applying quantum-computing methods.</small></td>
<td><small><em>What approaches have been proposed in the literature to simplify extremely large quantum circuits?</em></small></td>
<td align="right"><small><strong>34</strong><br>1.2%</small></td>
</tr>
<tr>
<td><small><strong>Error</strong></small></td>
<td><small>Discussions centered on explicit errors or failures encountered when developing, compiling, transpiling, or executing quantum programs, including exceptions, unexpected outputs, and malfunctioning code.</small></td>
<td><small><code>ValueError: Operation does not satisfy the given keep condition but cannot be decomposed.</code></small></td>
<td align="right"><small><strong>156</strong><br>5.7%</small></td>
</tr>
</tbody>
</table>

The percentages are calculated over all <strong>2,740</strong> analyzed forum posts. Each post is assigned to one concept according to its dominant discussion purpose.
