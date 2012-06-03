require 'erb'
require 'yaml'

data = YAML.load_file( "indicium_vitae.yaml" )

exec_template = lambda do |t|
  template = ERB.new(File.read( t.prerequisites[0] ), 0, ">")
  File.open(t.name, 'w') {|f| f.write(template.result(binding)) }
end

file data[:tex][:output] => data[:tex][:template], &exec_template
file data[:html][:output] => data[:html][:template], &exec_template

task :tex => data[:tex][:output]
task :pdf => data[:tex][:output] do
  `pdflatex #{data[:tex][:output]}`
end

task :clean do
  `rm -f *.tex`
  `rm -f *.log`
  `rm -f *.pdf`
  `rm -f _TZ_*`
end
