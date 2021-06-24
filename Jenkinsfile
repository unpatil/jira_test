properties([  
  parameters ([
    string(
        defaultValue: '', description: '', name: 'JIRA_ID'
      ),
      string(
        defaultValue: '', description: '', name: 'ATTACH_ID'
      ),
      string(
        defaultValue: '', description: '', name: 'FILE_NAME'
      )
  ])
])

pipeline {
  agent {
    node {
      label 'Slave1'
    }
  }      
  stages {
    stage('Get_Jira_Issue') {
      steps {
        node('Slave1') {
          script {
            def issue = jiraGetIssue(idOrKey: '${JIRA_ID}', site: 'Jira_Stage')
            echo issue.data.toString()
          }
        }
      }
    }

    stage('Get_Attachment_Details') {
      steps {
        node('Slave1') {
          script {
            def attachment = jiraGetAttachmentInfo(site: 'Jira_Stage', id: '${ATTACH_ID}')
            echo attachment.data.toString()
          }
        }
      }
    }
    
    stage('Upload_Attachment') {
      steps {
        node('Slave1') {
          script {
            def attachment1 = jiraUploadAttachment(idOrKey: '${JIRA_ID}', file: '${FILE_NAME}', site: 'Jira_Stage')
            echo attachment1.data.toString()
          }
        }
      }
    }

  }
}
