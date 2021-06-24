pipeline {
  agent {
    node {
      label 'Slave1'
    }

  }
  stages {
    stage('Get_Jira_Issue') {
      steps {
        def issue = jiraGetIssue(idOrKey: 'TESTPROJ-575', site: 'Jira_Stage')
        echo issue.data.toString()
      }
    }

    stage('Get_Attachment_Details') {
      steps {
         def attachment = jiraGetAttachmentInfo(site: 'Jira_Stage', id: '1299634')
        echo attachment.data.toString()
      }
    }
    
    stage('Upload_Attachment') {
      steps {
        def attachment1 = jiraUploadAttachment(idOrKey: 'TESTPROJ-575', file: 'test.txt', site: 'Jira_Stage')
        echo attachment1.data.toString()
      }
    }

  }
}
