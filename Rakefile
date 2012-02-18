desc 'Default: Compile jekyll site and compass stylesheets'
task :default => ['compass:compile', 'jekyll:compile']

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
  SASS_DIR = '_sass'

  desc 'Delete compiled stylesheets'
  task :clean do
    system 'rm -rf stylesheets'
  end

  desc 'Compile sass scripts'
  task :compile => [:clean] do
    system "compass compile --sass-dir #{SASS_DIR}"
  end

  desc 'Run the compass watch server'
  task :server do
    system "compass watch --sass-dir #{SASS_DIR}"
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
