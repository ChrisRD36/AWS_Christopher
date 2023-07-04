pipeline {
   agent {
     label "linux-agent"
    }

   environment {
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
              sh 'ls -la'
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
