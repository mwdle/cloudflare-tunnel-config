@Library("JenkinsPipelines") _ // See https://github.com/mwdle/JenkinsPipelines

// Disable index triggers on branches that are not main/master
boolean isMainBranch = (env.BRANCH_NAME == 'main' || env.BRANCH_NAME == 'master')
boolean disableIndexTriggers = !isMainBranch

quadletPipeline(
    disableIndexTriggers: disableIndexTriggers,
    alertEmail: "${env.ALERT_EMAIL}",
    podmanSecretMappings: [
        [
            type: 'string',
            credentialsId: 'cloudflare-tunnel-token',
            podmanSecretStringName: 'cloudflare_tunnel_token'
        ]
    ]
)
