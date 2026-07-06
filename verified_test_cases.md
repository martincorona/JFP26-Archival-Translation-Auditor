# Verified Test Cases

Below are actual outputs from the evaluation pipeline, demonstrating how the framework caught specific translation failures across Google Translate, GPT-3.5, and GPT-4.0 using the 1848 Treaty of Guadalupe Hidalgo text.

### Test Case 1: Google Translate (Idiomatic Failure)
* **Original Spanish:** "Tratado de paz, amistad limites y arreglo definitivo..."
* **Ground Truth English:** "Treaty of Peace, Friendship, Limits and Settlement..."
* **Target Output:** "Treaty of peace, friendship, limits and definite arrangement..."
* **Auditor Verdict:** FAIL. Flagged for **Idiomatic Failure**. The target translation literally translated "arreglo definitivo" to "definite arrangement," which loses the formal, legal meaning of a diplomatic "Settlement."

### Test Case 2: GPT-3.5 (Temporal Drift)
* **Original Spanish:** "...animados de un sincero deseo de poner término a las calamidades de la guerra..."
* **Ground Truth English:** "...animated by a sincere desire to put an end to the calamities of the war..."
* **Target Output:** "...driven by a sincere goal to terminate the negative impacts of the conflict..."
* **Auditor Verdict:** FAIL. Flagged for **Temporal Drift**. The translation replaces 19th-century diplomatic phrasing with modern corporate jargon ("terminate the negative impacts"). 

### Test Case 3: GPT-4.0 (Fact Alteration via Localization)
* **Original Spanish:** "La línea divisoria entre las dos Repúblicas comenzará en el golfo de México, tres leguas fuera de tierra frente a la desembocadura del río Grande..."
* **Ground Truth English:** "The boundary line between the two Republics shall commence in the Gulf of Mexico, three leagues from land, opposite the mouth of the Rio Grande..."
* **Target Output:** "The boundary line between the two Republics will start in the Gulf of Mexico, three miles from land, opposite the mouth of the Rio Grande..."
* **Auditor Verdict:** FAIL. Flagged for **Fact Alteration**. While the grammar and tone were accurate, the model attempted to localize the historical measurement, swapping the 1848 distance of "three leagues" for the modern measurement of "three miles," permanently altering a critical geographic boundary coordinate.
