pipeline {
  agent {
    node {
      label 'Slave1'
    }

  }
  stages {
    stage('Get_Jira_Issue') {
      steps {
        jiraGetIssue(idOrKey: 'TESTPROJ-575', site: 'Jira_Stage')
      }
    }

    stage('Get_Attachment_Details') {
      steps {
        jiraGetAttachmentInfo(site: 'Jira_Stage', id: 'TESTPROJ-575')
      }
    }

    stage('Upload_Attachment') {
      steps {
        jiraUploadAttachment(idOrKey: 'TESTPROJ-575', file: 'test.txt', site: 'Jira_Stage')
      }
    }

  }
}