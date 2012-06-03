require 'erb'
require 'yaml'

data = YAML.load_file( "indicium_vitae.yaml" )

def exec_template(task, data)
  template_path = File.expand_path(File.join(data[task][:template]))
  template = ERB.new(File.read( template_path ), 0, ">")

  f = File.new( data[task][:output], "w" )
  f.write(template.result(binding))
  f.close
end

task :tex do
  exec_template(:tex, data)
end

task :pdf => :tex do
  `pdflatex #{data[:tex][:output]}`
end

task :html do
  exec_template(:html, data)
end

task :clean do
  `rm -f *.tex`
  `rm -f *.log`
  `rm -f *.pdf`
  `rm -f _TZ_*`
end
