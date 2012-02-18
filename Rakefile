desc 'Default: Start jekyll server'
task :default => 'jekyll:server'

namespace :jekyll do
  desc 'Remove generated site'
  task :clean do
    system 'rm -rf _site'
  end

  desc 'Start jekyll server'
  task :server do
    system 'jekyll --server --auto'
  end
end

namespace :compass do
  desc 'Delete compass temporary files'
  task :clean do
    system 'rm -rf css/*'
  end

  desc 'Run the compass watch script'
  task :watch do
    system 'compass watch'
  end

  desc 'Compile sass scripts'
  task :compile => [:clean] do
    system 'compass compile'
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
