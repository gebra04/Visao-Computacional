# AcralNet: Detecção de Melanoma Acral com EfficientNet-B0

## 📌 Sobre o Projeto
Este projeto de Visão Computacional utiliza *Deep Learning* para a classificação de lesões de pele acrais (palmas, plantas e leitos ungueais), diferenciando melanomas malignos de lesões benignas. 

Devido à natureza única da pele acral (como o padrão de cristas paralelas), o modelo foi otimizado para evitar viés de artefato e maximizar a sensibilidade médica.

## ⚙️ Metodologia e Arquitetura
* **Modelo Base:** `EfficientNet-B0` escolhida pelo seu baixo custo computacional (*Compound Scaling*) e resistência ao *overfitting* em datasets médicos restritos.
* **Pipeline de Treinamento:** Iniciou com *Transfer Learning* (ImageNet) e evoluiu para *Full Fine-Tuning* com taxa de aprendizado otimizada (`1e-4`) e Dropout de `0.4`.
* **Data Augmentation Específico:** Transformações on-the-fly em ambas as classes simultaneamente (Rotação 360º, Translações, Zoom) usando preenchimento `reflect` para manter a continuidade matemática dos sulcos da pele.
* **Métrica Médica (Soberania do Recall):** O sistema utiliza callbacks avançados (`EarlyStopping`, `ReduceLROnPlateau`) e salva o melhor modelo através de um `ModelCheckpoint` ancorado no **Recall de Validação**, minimizando a chance de falsos negativos (pacientes com câncer não diagnosticados).

## 🛠️ Tecnologias Utilizadas
* Python
* TensorFlow / Keras
* Pandas & Scikit-Learn
* Matplotlib & Seaborn (Análise de Matriz de Confusão)