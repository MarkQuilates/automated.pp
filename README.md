#INSTALL PACKAGES
class vim { 
package { 'vim':
ensure => 'installed',
}
}

class curl { 
package { 'curl':
ensure => 'installed',
}
}

class git { 
package { 'git':
ensure => 'installed',
}
}


#USER
user {'monitor':
home =>'/home/monitor',
shell =>'/bin/bash',
}


#DIRECTORY
file { [ '/home', '/home/monitor', /home/monitor/scripts' ]:
ensure =>'directory',
}

class fetch_file {
include::wget
wget::fetch { 'https://github.com/MarkQuilates/memory_check/blob/master/READ.md':
destination =>'home/monitor/scripts',
timeout => 15,
verbose => true,
}
}
