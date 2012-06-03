require 'erb'
require 'yaml'

data = YAML.load_file( "indicium_vitae.yaml" )

task :tex do
  template_path = File.expand_path(File.join("templates/cv.tex.erb"))
  template = ERB.new(File.read( template_path ), 0, ">")

  f = File.new( data[:tex][:output], "w" )
  f.write(template.result(binding))
  f.close
end

task :pdf => :tex do
  `pdflatex #{data[:tex][:output]}`
end

task :html do

end

task :clean do
  `rm -f *.tex`
  `rm -f *.log`
  `rm -f *.pdf`
  `rm -f _TZ_*`
end
