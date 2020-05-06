library identifier: 'ARM-PIt-libraries@master',
retriever: modernSCM(
  [
    $class: 'GitSCMSource',
    credentialsId: 'cedb6908-8b3d-49a3-9137-a086e65920c3',
    remote: 'git@github.com:ARM-PIt/jenkins-shared-library.git',
    traits:  [[$class: 'jenkins.plugins.git.traits.BranchDiscoveryTrait']]
  ]
)

properties(
  [
    parameters(
      [
        choice(
          name: 'build_type',
          defaultValue: 'nightly',
          choices: ['adhoc','nightly','weekly'].join('\n'),
          description: 'Which build type is this? (adhoc, nightly, weekly)',
        )
      ]
    )
  ]
)

pipelineChrootToDockerToRegistry project_git_url: "git@github.com:ARM-PIt/debian-10-armhf.git", 
project_git_branch: "master",
distro: "debian",
build_type: "${build_type}",
image_name: "debian-10-armhf",
registry_path: "armpits",
registry_url: "https://docker.io",
apt_url: "http://deb.debian.org/debian",
apt_key_url: "https://ftp-master.debian.org/keys/release-10.asc",
apt_options: "buster main buster-updates"
