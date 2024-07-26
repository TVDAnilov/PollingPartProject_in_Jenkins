pipeline {
    agent any

    stages {
        stage('Загрузка изменений из Git') {
steps{
checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/TVDAnilov/PollingPartProject_in_Jenkins.git']])
	}}
	stage('Check Changes') {
            steps {
                script {
                    def hasChanges = false

                    // Проверка изменений в директории project1
                    if (changeset("Folder4/**")) {
                        hasChanges = true
                    }
                    // Если изменений нет, завершить пайплайн с ошибкой
                    if (!hasChanges) {
			powershell 'Write-Host "No changes detected in any project directories. Exiting the pipeline"'
                        currentBuild.result = 'ABORTED'
                        error("No changes detected in any project directories. Exiting the pipeline.")
                    }
                }
            }
        }
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
	//aborted {
         //   script {
                // Удаление сборки, если пайплайн был прерван из-за отсутствия изменений
          //      if (currentBuild.result == 'ABORTED') {
           //         def buildNumber = currentBuild.number
           //         println "Deleting aborted build #${buildNumber} due to no changes detected."
            //        currentBuild.rawBuild.delete()
            //    }
           // }
          //}
        }
        
    
}