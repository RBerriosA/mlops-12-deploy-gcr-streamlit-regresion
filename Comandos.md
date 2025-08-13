## Paso 0: Vinculación
gcloud init

## Paso 1: Creación del repositorio
gcloud artifacts repositories create repo-mlops12-api-streamlit-m2s6-modelo-pycaret --repository-format docker --project project-mlops12-rafael-berrios --location us-central1

## A mano

## Paso 2: Crear la imagen de mi APLICACION y subir al repositorio
gcloud builds submit --config=cloudbuild.yaml --project project-mlops12-rafael-berrios

## Paso 3: Comando para despliegue o ejecución de la imagen en el repositorio
gcloud run services replace service.yaml --region us-central1 --project project-mlops12-rafael-berrios

## Paso 4: OPCIONAL, Dar permisos de acceso a mi APLICACION. ESTO SE EJECUTA UNA SOLA VEZ
gcloud run services set-iam-policy servicio-api-mlops12-m2s1-rafael-berrios gcr-service-policy.yaml --region us-central1 --project project-mlops12-rafael-berrios

## Automatizacion

git init
git add . 
git commit -m "Proyecto de automatización de despliegue en GCR con pycaret M2S6"
git branch -M main
git remote add origin https://github.com/RBerriosA/mlops-12-deploy-gcr-streamlit-regresion.git
git push -u origin main