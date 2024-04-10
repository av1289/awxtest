pipeline {
  agent any
  stages {
    stage('dev') {
      parallel {
        stage('dev') {
          steps {
            ansibleTower(towerServer: 'AWX', jobTemplate: '10', importTowerLogs: true, extraVars: 'services_to_check:   - Spooler restart_services: true', verbose: true)
          }
        }

        stage('test') {
          steps {
            ansibleTower(towerServer: 'AWX', jobTemplate: '10', inventory: 'windows', importTowerLogs: true, extraVars: 'services_to_check:   - Spooler restart_services: false', throwExceptionWhenFail: true, templateType: 'Import Full Logs', verbose: true)
          }
        }

      }
    }

  }
}