pipeline {
    agent any

    stages {

        stage('Приветствие') {
            steps {
                powershell 'Write-Host "Привет, мир!"'
            }
        }

        stage('Сборка') {
            steps {
                powershell 'Write-Host "Выполняется сборка...!"'
                // Добавьте команды для сборки вашего проекта
            }
        }

        stage('Тесты') {
            steps {
                powershell 'Write-Host "Выполняются тесты...!"'
                // Добавьте команды для запуска тестов!
            }
        }
    }
        post('Сообщение после сборки') {
            success{
                archiveArtifacts artifacts: '/**/*', followSymlinks: false
                powershell 'Write-Host "Сборка завершена!"'
                // Добавьте команды для отправки сообщения после сборки
            }
        }
        
    
}