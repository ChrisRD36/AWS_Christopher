pipeline {
   agent {
     label "linux-agent"
    }

   environment {
       AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_IDC')
       AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEYC')
       AWS_DEFAULT_REGION = 'us-east-2'
       lista_correo = 'devopschrisrd@gmail.com'
       texto_correo = "El pipeline ${build_url}."
       texto_correo2 = "El pipeline ${build_url} no se creo correctamente."
       subject_correo = "Detalles pipeline ${build_url}"
   }

   stages{
       stage('Instalar Dependencias'){
           steps{
              sh 'npm install'
            }  
           }
       stage('Compilacion del app'){
           steps{
              sh 'npm run build'
           }
       }

       stage('Mostrar Archivos'){
           steps{
              sh 'ls -la dist'
           }
          }

       stage('Deploy to AWS'){
           steps{
              sh 'aws s3 cp dist/angular-app/ s3://proyectoawschristopher --recursive'
           }
       }

       }

   post {
       success {
          emailext body: "${texto_correo} funciono sin problemas", subject: "${subject_correo}", to: "${lista_correo}"
       }
       failure {
          emailext body: "${texto_correo2} fallo, verificar errores", subject: "${subject_correo}", to: "${lista_correo}"
       }
       
   }
}
