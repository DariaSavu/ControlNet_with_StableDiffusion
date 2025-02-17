## Scopul proiectului
Prin acest proiect ne-am propus sa evaluam un model de stable diffusion la care au fost adaugate blocuri de control conditional pentru un task specializat- generarea imaginilor de design interior.
Ne-am folosit de modele preantrenate, bazate pe stable diffusion 1.5, in care imaginile de control erau cu segmentarea semantica a imaginii originale sau cu edge-urile acesteia.

Modelele au fost obtinute de aici: https://huggingface.co/lllyasviel/ControlNet/tree/main/models

Am antrenat in continuare aceste modele pe datasetul NYU Depth V2: https://cs.nyu.edu/~fergus/datasets/nyu_depth_v2.html folosind prompt-uri de tip text goale si imagini de control in doua variante: segmentarea semantica si edge-urile extrase din imaginea initiala.

## Rezultate

Am evaluat modelul prin calcularea FID-ului (Frechet Inception Distance) si a loss-ului. Cele mai bune rezultate au fost obtinute pentru imagini de control cu segmentarea semantica, si urmatoarele valori ale hiperparametrilor:

| Image Shape | Learning Rate | Batch Size | Epochs | Loss          |
|-------------|---------------|------------|--------|---------------|
| 128x128x3   | 1e-5          | 128        | 10     | ![Loss1](https://github.com/DariaSavu/ControlNet_with_StableDiffusion/blob/main/loss2.png)|
| 256x256x3   | 1e-5          | 64         | 12     | ![Loss2](https://github.com/DariaSavu/ControlNet_with_StableDiffusion/blob/main/loss1.png)|
