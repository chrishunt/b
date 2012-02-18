desc 'Clean jekyll and compass build files'
task :clean => ['jekyll:clean', 'compass:clean']

desc 'Compile jekyll site and compass stylesheets'
task :compile=> ['compass:compile', 'jekyll:compile']

desc 'Default: Start jekyll server'
task :default => 'jekyll:server'

namespace :jekyll do
  desc 'Remove generated site'
  task :clean do
    system 'rm -rf _site'
  end

  desc 'Compile jekyll site'
  task :compile do
    system 'jekyll'
  end

  desc 'Start jekyll server'
  task :server do
    system 'jekyll --server --auto'
  end
end

namespace :compass do
  desc 'Delete compass temporary files'
  task :clean do
    system 'rm -rf stylesheets'
  end

  desc 'Run the compass watch script'
  task :watch do
    system 'compass watch --sass-dir _sass'
  end

  desc 'Compile sass scripts'
  task :compile => [:clean] do
    system 'compass compile --sass-dir _sass'
  end
end

namespace :pygments do
  PYGMENTS_DIR = '_sass/pygments'

  desc 'Delete pygments CSS files'
  task :clean do
    system "rm -f #{PYGMENTS_DIR}/*.scss"
  end

  desc 'Generate pygments CSS'
  task :compile => [:clean] do
    system "mkdir -p #{PYGMENTS_DIR}"
    system "pygmentize -S solarized -f html > #{PYGMENTS_DIR}/solarized.scss"
  end
end
