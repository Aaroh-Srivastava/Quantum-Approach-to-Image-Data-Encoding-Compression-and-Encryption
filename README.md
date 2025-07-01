# Quantum-Approach-to-Image-Data-Encoding-Encryption-and-Encryption

The rapid growth of data generation, especially in image data, necessitates efficient encoding and processing techniques. Traditional methods struggle to handle the volume and complexity of image data. This project aims to develop quantum-inspired algorithms for encoding image data, using concepts like quantum superposition and entanglement. It also investigates quantum-inspired methods for image compression and encryption to improve data storage and security in image-based applications.The research methodology includes theoretical analysis, algorithm design, and practical implementation using quantum computing simulators and hardware. Comparative studies will evaluate the performance and effectiveness of the proposed quantum-inspired approaches.

Coding Launguage Used- Python.
Libraries Used- Qiskit, Pennylane, Numpy, Matplotlib, Pandas, cv2, Qiskit_aer, Crypto, AES.

**Encoding Techniques:**
1.	Basic Encoding: The most basic form of encoding classical binary data (0s and 1s) into qubits. A classical data value with n binary bits is encoded using basic state of n qubits in basic embedding.  Each classical bit is mapped to a computational  basis state i.e., 0 to |0⟩ and 1 to |1⟩.

2.	Phase Encoding: Data is encoded into the phase of quantum states. The angle embedding encodes n classical features into a minimum of n qubits, where each feature is encoded as a rotational angle of a quantum rotational gate. A classical bit 0 or 1 is mapped as:
                                                                                                           0 → |0⟩
                                                                                                           1 → e^{iθ} |0⟩

3.	Amplitude Encoding: Classical data is encoded into the amplitude of the quantum state. A normalized vector X = (x₁, x₂, ..., xₙ) is mapped into a quantum superposition: ∣ψ⟩=x1∣0⟩+x2∣1⟩+...+xn∣n−1⟩. It is useful in quantum fourier transform (QFT) and interference-based algorithms.

**Compression Techniques:**
1.	QCT1: Amplitude embedding with direct Pauli-Z measurement
        •	Initial Qubit State: All qubits initialized to ∣0⟩.
        •	Transformation Applied: None (no gate operations post-embedding).
        •	Measurement Operator: Pauli-Z
2.	QCT2: Amplitude embedding with Pauli-X transformation.
        •	Initial Qubit State: All qubits initialized to ∣0⟩.
        •	Transformation Applied: Pauli-X gate applied after embedding.
        •	Measurement Operator: Pauli-Z
3.	QCT3: Amplitude embedding with qubit entanglement.
        •	Initial Qubit State: All qubits start to ∣0⟩.
        •	Transformation Applied: CNOT gates to entangle 4 quantum wires.
        •	Measurement Operator: Pauli-Z
4.	QCT4: Hybrid quantum processing with embedding, transformation and entanglement.
        •	Initial Qubit State: All qubits start to ∣0⟩.
        •	Transformation Applied: Pauli-X gate followed by CNOT entanglement.
        •	Measurement Operator: Pauli-Z.

This is the latest addition to the research which includes comparison of quantum and classical compression techniques and comparing the feasibility of them. Classical encryption techniques includes AES-128, AES-256 and there exists encryption breaking  algorithms in quantum computing, i.e., Shor’s algorithm, Groover’s algorithm which by-passes few of the classical encryption methods. Finally the encrypted image file is decrypted using the key on the receiver end and the original compressed image is attained.

**Classical Encryption Techniques**
Classical encryption techniques are methods used to secure data using mathematical transformations. AES is one of the strongest classical encryption technique. AES(Advanced Encryption Standard) is the symmetric key block cipher that encrypts and decrypts data using a 256-bit key. AES follows the Substitution-Permutation Network (SPN) architecture. It encrypts data in 14 rounds, applying multiple transformations to ensure high security. 
1.	Key expansion: The 256-bit key is expanded into 15 rounds.
2.	AddRoundKey (Pre-Round Transformation): XOR the plaintext block with the first block key.
3.	Main Rounds: Each round consists 4 transformations; SubBytes, ShiftRows, MixColumns, AddRoundKey.
4.	Final Round: Finally AddRoundKey step is implemented.

AES-128 works with 10 rounds. 2¹²⁸ possible keys are generated which makes its highly secure. It is used majorly in commercial-grade security. AES-256 works with 14 rounds. It has 2²⁵⁶ possible keys making it more secure that AES-128. Used by military and government organization.

**Quantum Encryption-Breaking Algorithms**
Quantum encryption leverages the principles of quantum mechanics- superposition, entanglement and no-cloning scheme to create secure communication channels. It provides provable security based on physics, Quantum eavesdropping detection due to which any interception disturbs the system.

Shor’s Algorithm, is a quantum algorithm designed to efficiently factor large numbers into their prime components. Modern classical encryption RSA depends  on the fact that factoring large numbers is classically hard, which can be easily broken by Shor’s algorithm.

Groover’s Algorithm, is a search algorithm that finds a target in an unsorted space with quadratic speedup over classical method. It searches through unsorted database  in O(√N) time, where classical  search takes O(N) time. Speeds up brute-force attacks by reducing number of operations from 2ⁿ to 2ⁿ/².

**Selection of Encryption Technique**
AES-128 is strong individually but placed against certain advanced algorithms like Groover’s can make it less secure. Brute-force attack time reduces from 2¹²⁸ → 2⁶⁴ (Extremely weak). 

In AES-256, found to be more quantum-resistant. Brute-force attack time reduces from 2²⁵⁶ → 2¹²⁸ (Extremely strong). AES-256 uses a stronger key expansion mechanism than AES-128. A quantum computer strong enough to break AES-256 does not exist. 

**RESULTS AND OBSERVATIONS**
The test was conducted using the Qiskit and Pennylane module in python. The dataset included a set of SAR images to see the performance on a wider range. First we down-sized the image to from its original size (800x800) to 400x400 to meet the computational resource of the current quantum computer. The initial state of all qubits are set to 0 by default. The pixel values are encoded into the QEC using amplitude encoding technique. The encoded data is further processed by the quantum compression techniques QCT1 in which the quantum data is measured using the Pauli-Z operator to convert back to classical domain in the range [-1,1], which is further normalized back to the range of [0,255]. Hence, this method theoretically compressed by 60-70%. 
The overall effect of the circuit can be studied using the compression techniques QCT1, QCT2, QCT3 and QCT4. This study analysis the result on the basis of a visual metrics and a compression ratio to see the difference of input and output. And finally a theoretical study on the most optimal encryption technique. 

As shown previous, theoretical compression ratio is shown to be 4:1 but after practical implementation analysing the 4 techniques on the dataset, it is observed that the result is closer to 4:1 ratio but still on the lesser range. Additionally, compression on SAR image is seen to be better than on ordinary image due to SAR being a grayscale image.  From Table I, it can be observed that the size is reduced to about 75% of the original image size. 
![image](https://github.com/user-attachments/assets/e03574cf-b82d-433d-97ab-747dc24d1bfd)

4 parameters are used for objective evaluation of the compressed images. They are relative variance (RV), peak signal to noise ratio (PSNR), structural similarity index measure (SSIM), and universal image quality index (UIQI).
![image](https://github.com/user-attachments/assets/fa6325b5-fe0f-4e1d-84dc-2ef66b6c29a6)

It can be observed that the RV of QCT-1 is the best out of all since it should be as close to 1 as possible. While QCT-4 shows the best signal to noise ratio. Overall after comparing all the 4 techniques it can be observed that QCT-4 is the better compression technique out of the four.

**Encryption Method**
In this study, AES-256 encryption was implemented to secure image data, following the reasoning presented by Grassl, Langenberg, Roetteler, and Steinwandt, who demonstrated that even advanced quantum algorithms like Grover’s are not yet capable of breaking AES-256 encryption due to the enormous quantum resources required [3]. Based on these findings, AES-256 was chosen as the encryption approach in this work to ensure strong data protection. After encryption, the image was transformed into a binary file that no longer retained any visible characteristics and appeared as random, unreadable noise. The encryption process also generated a 32-byte key, as specified in the AES-256 standard, which is required to accurately decrypt and recover the original image.

**Conclusion**
This study examined three quantum data encoding techniques — Basis Embedding, Angle Embedding, and Amplitude Embedding — for processing high-resolution satellite images. While Basis Embedding is simple, it demands a large number of qubits, limiting its scalability. Angle Embedding offers better qubit efficiency but struggles with high-dimensional image data. Amplitude Embedding proved to be the most effective, enabling complex datasets to be encoded with minimal qubit resources, making it ideal for quantum image processing applications.

Additionally, AES-256 remains one of the strongest encryption standards available, offering a 256-bit key space that makes brute-force attacks computationally infeasible with classical machines. Even in the face of quantum algorithms like Grover’s, which reduce effective security to 128 bits, AES-256 continues to provide strong protection. This highlights its reliability as a future-resilient encryption method, offering both present-day security and robustness against emerging quantum threats.
