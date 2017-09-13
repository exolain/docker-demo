node("docker") {
    docker.withRegistry('https://hub.docker.com/r/exolain/registry-nmarinpe/', 'exolain') {
    
        git url: "https://github.com/exolain/docker-demo", credentialsId: 'exolain'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "docker-demo"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
