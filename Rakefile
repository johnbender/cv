require 'erb'
require 'yaml'

data = YAML.load_file( "indicium_vitae.yaml" )

exec_template = lambda do |task|
  template_path = File.expand_path(File.join(data[task][:template]))
  template = ERB.new(File.read( template_path ), 0, ">")

  f = File.new( data[task][:output], "w" )
  f.write(template.result(binding))
  f.close
end

task :tex do
  exec_template.call(:tex)
end

task :pdf => :tex do
  `pdflatex #{data[:tex][:output]}`
end

task :html do
  exec_template.call(:html)
end

task :clean do
  `rm -f *.tex`
  `rm -f *.log`
  `rm -f *.pdf`
  `rm -f _TZ_*`
end
