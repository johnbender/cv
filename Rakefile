require 'erb'
require 'yaml'

data = YAML.load_file( "indicium_vitae.yaml" )

exec_template = lambda do |t, args|
  data[:public] = ENV['PUBLIC']
  template = ERB.new(File.read( t.prerequisites[0] ), 0, ">")
  File.open(t.name, 'w') {|f| f.write(template.result(binding)) }
end

file data[:tex][:output] => data[:tex][:template], &exec_template
file data[:html][:output] => data[:html][:template], &exec_template

task :html => data[:html][:output]
task :tex => data[:tex][:output]
task :pdf => data[:tex][:output] do
  `pdflatex #{data[:tex][:output]} #{data[:tex][:pdf]}`
end

task :default => [:pdf, :html]

task :clean do
  `rm -f *.tex *.log *.pdf _TZ_* *.html`
end

task :"gh-pages" => [:html, :pdf] do
  Kernel.exec(<<-CMD)
    set -e
    git checkout gh-pages
    mv #{data[:html][:output]} index.html
    mv #{data[:tex][:pdf]} cv-`date +%Y-%m`.pdf
    git add .
    git commit -m 'index page update'
    git checkout master
  CMD
end
