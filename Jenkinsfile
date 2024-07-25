pipeline {
    agent any

    stages {
        stage('Загрузка изменений из Git') {
            steps {
checkout scmGit(
branches: [[name: '*/main']], extensions:
	 [[$class: 'SparseCheckoutPaths', sparseCheckoutPaths: [[path: '/Folder4/Folder_in_folder4_4/']]]]
userRemoteConfigs: [[url: 'https://github.com/TVDAnilov/PollingPartProject_in_Jenkins.git']])
            }
        }
        stage('Приветствие') {
            steps {
                powershell 'Write-Host "Привет, мир!"'
            }
        }

        stage('Сборка') {
            steps {
                powershell 'Write-Host "Выполняется сборка..."'
                // Добавьте команды для сборки вашего проекта
            }
        }

        stage('Тесты') {
            steps {
                powershell 'Write-Host "Выполняются тесты..."'
                // Добавьте команды для запуска тестов
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