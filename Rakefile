require 'rubygems'

require 'debian/build'
include Debian::Build

require 'debian/build/config'

namespace "package" do
  Package.new("cruisecontrolrb") do |t|
    t.version = '1.4.0+git200912231806'
    t.debian_increment = 1

    t.source_provider = DebianTarballProvider.new
  end

  namespace "cruisecontrolrb:source:update" do
    desc "Update source tarball with current git sources"
    task :git do
      name = "cruisecontrolrb"
      base_version = "1.4.0"
      version="#{base_version}+git#{Time.now.strftime('%Y%m%d%H%M')}"

      tmp_dir="/tmp/#{name}.git"
      sources_dir="#{tmp_dir}/#{name}-#{base_version}"

      rm_rf tmp_dir
      mkdir_p sources_dir

      sh "wget -O - http://github.com/thoughtworks/cruisecontrolrb/tarball/master | tar -xzf - --strip 1 -C #{sources_dir}"
      sh "tar -czf '#{name}-#{version}.tgz' -C #{tmp_dir} ."
      rm_rf tmp_dir

      sh "dch --newversion '#{version}-1' 'New upstream release'"
    end
  end

end


require 'debian/build/tasks'

