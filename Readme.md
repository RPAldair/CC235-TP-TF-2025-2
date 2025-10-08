# Sistema de Clasificación de Radiografías Torácicas COVID-19

## Descripción del Proyecto

Sistema inteligente de procesamiento y clasificación de imágenes radiográficas para el diagnóstico asistido de COVID-19, Neumonía Viral y Opacidad Pulmonar, utilizando técnicas clásicas de procesamiento de imágenes y Deep Learning.

**Curso:** CC235 - Procesamiento de Imágenes  
**Ciclo:** 2025-02  
**Universidad:** [Tu Universidad]

---

## 👥 Integrantes del Equipo

1. César Gabriel Avalos Sánchez		-	u202310307
2. Fabian Marcelo Rojas Cuadros		-	u202218498
3. Leonardo Franco Gamboa Huilcaya	-	u202322950
4. Piero Aldair Rivas Pinto			-	u202122405

---

## Objetivos

### Objetivo General
Desarrollar un sistema automatizado que aplique técnicas de procesamiento digital para realzar, segmentar y clasificar radiografías torácicas en cuatro categorías: COVID-19, Neumonía Viral, Opacidad Pulmonar y Normal.

### Objetivos Específicos
1. Implementar técnicas clásicas de realce de imágenes (CLAHE, filtros espaciales)
2. Aplicar métodos de segmentación (Otsu, Canny, morfología matemática)
3. Desarrollar un modelo de clasificación con técnicas tradicionales (SVM, Random Forest)
4. Implementar un modelo de Deep Learning con Transfer Learning (ResNet50)
5. Comparar el rendimiento de ambos enfoques mediante métricas estándar

---

## Preguntas de Investigación

1. **Clasificación Principal:** ¿La radiografía corresponde a COVID-19, Neumonía Viral, Opacidad Pulmonar o Normal?
2. **Evaluación de Calidad:** ¿La imagen procesada presenta calidad diagnóstica adecuada tras el realce?
3. **Segmentación Regional:** ¿En qué zona pulmonar (superior, media o inferior) se localiza la mayor afectación?

---

## Dataset

**Fuente:** [COVID-19 Radiography Database](https://www.kaggle.com/datasets/tawsifurrahman/covid19-radiography-database) (Kaggle)

### Composición
- **COVID-19:** 3,616 imágenes
- **Lung Opacity:** 6,012 imágenes
- **Viral Pneumonia:** 1,345 imágenes
- **Normal:** 10,192 imágenes
- **Total:** 21,165 radiografías

### Características
- **Formato:** PNG
- **Resolución:** Variable (299×299 a 1024×1024 píxeles)
- **Tipo:** Escala de grises / RGB
- **Origen:** Repositorios médicos públicos internacionales

---

## Metodología

### 1. Preprocesamiento
- Redimensionamiento a 256×256 píxeles
- Conversión a escala de grises
- Normalización de intensidades [0, 1]
- Filtrado de ruido (Gaussiano, Mediana)

### 2. Realce de Imágenes
- **CLAHE** (Contrast Limited Adaptive Histogram Equalization)
- **Unsharp Masking** para nitidez
- Ajuste de brillo y contraste

### 3. Segmentación
- Umbralización de Otsu
- Detección de bordes (Canny, Sobel)
- Operaciones morfológicas (erosión, dilatación)

### 4. Modelos Implementados

#### Modelo Clásico
```
Realce → Segmentación → Extracción Features → Clasificación
                         (HOG, LBP, GLCM)      (SVM / Random Forest)
```

**Características extraídas:**
- HOG (Histogram of Oriented Gradients)
- LBP (Local Binary Patterns)
- GLCM (Gray-Level Co-occurrence Matrix)
- Estadísticas del histograma

#### Modelo Deep Learning
```
ResNet50 (ImageNet) → Fine-tuning → Clasificación (4 clases)
```

**Arquitectura:**
- Base: ResNet50 preentrenada
- Global Average Pooling
- Dense(512) + Dropout(0.5)
- Dense(256) + Dropout(0.3)
- Softmax(4)

**Entrenamiento:**
- Optimizador: Adam (lr=1e-4)
- Data Augmentation
- Early Stopping
- ReduceLROnPlateau

---

## Referencias Bibliográficas

1. ACT Accelerator Ethics & Governance Working Group. (2020, 28 mayo). Ethical considerations to guide the use of digital proximity tracking technologies for COVID-19 contact tracing. Recuperado de https://www.who.int/publications/i/item/WHO-2019-nCoV-Ethics_Contact_tracing_apps-2020.1 
2. Can AI Help in Screening Viral and COVID-19 Pneumonia? (2020). IEEE Journals & Magazine | IEEE Xplore. Recuperado de  https://ieeexplore.ieee.org/document/9144185 
3. Deep Residual Learning for Image Recognition. (2016, 1 junio). IEEE Conference Publication | IEEE Xplore. Recuperado de https://ieeexplore.ieee.org/document/7780459 
4. Gonzalez, R. C., & Woods, R. E. (2018). Digital Image Processing (4th ed.). Pearson. Recuperado de https://www.cl72.org/090imagePLib/books/Gonzales,Woods-Digital.Image.Processing.4th.Edition.pdf
5. Histograms of oriented gradients for human detection. (2005). IEEE Conference Publication | IEEE Xplore. Recuperado de  https://ieeexplore.ieee.org/document/1467360
6. He, K., Zhang, X., Ren, S., & Sun, J. (2016). Deep Residual Learning for Image Recognition. Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 770-778. Recuperado de https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/He_Deep_Residual_Learning_CVPR_2016_paper.pdf
7. Chowdhury, M. E. H., Rahman, T., Khandakar, A., Mazhar, R., Kadir, M. A., Mahbub, Z. B., Islam, K. R., Khan, M. S., Iqbal, A., Emadi, N. A., Reaz, M. B. I., & Islam, M. T. (2020). Can AI Help in Screening Viral and COVID-19 Pneumonia? IEEE Access, 8, 132665-132676. Recuperado de https://doi.org/10.1109/access.2020.3010287
8. Rahman, T., Khandakar, A., Qiblawey, Y., Tahir, A., Kiranyaz, S., Kashem, S. B. A., Islam, M. T., Maadeed, S. A., Zughaier, S. M., Khan, M. S., & Chowdhury, M. E. (2021). Exploring the effect of image enhancement techniques on COVID-19 detection using chest X-ray images. Computers In Biology And Medicine, 132, 104319. Recuperado de https://doi.org/10.1016/j.compbiomed.2021.104319
9. Rahman, T. (2022). COVID-19 Radiography Database [Conjunto de datos]. En M. Chowdhury & A. Khandakar (Eds.), Kaggle. https://www.kaggle.com/datasets/tawsifurrahman/covid19-radiography-database
10. Rajpurkar, P., et al. (2017). CheXNet: Radiologist-Level Pneumonia Detection on Chest X-Rays with Deep Learning. arXiv preprint arXiv:1711.05225. Recuperado de https://arxiv.org/abs/1711.05225
11. Rahimzadeh, M., & Attar, A. (2020). A modified deep convolutional neural network for detecting COVID-19 and pneumonia from chest X-ray images. Informatics in Medicine Unlocked, 19, 100360. Recuperado de https://www.sciencedirect.com/science/article/pii/S2352914820302537



## 📝 Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo `LICENSE` para más detalles.

**Nota:** El dataset COVID-19 Radiography Database está disponible bajo licencia abierta exclusivamente para fines académicos y de investigación.


**Última actualización:** Octubre 2025
