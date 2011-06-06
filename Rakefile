
require 'albacore'

task :default => [:solutionbuild,:spec,:buildwrap,:publishwrap]

desc "Solution build"
msbuild :solutionbuild do |msb|	
    msb.properties :configuration => "Release"
    msb.targets :Clean, :Build
    msb.solution = "./src/Castle.Windsor.Lifestyles.sln"
end

desc "NUnit Tests"
nunit :spec do |nunit|
	nunit.command = "./lib/nunit/nunit-console.exe"
	nunit.assemblies "./src/Castle.Windsor.Lifestyles.Tests/bin/Release/Castle.Windsor.Lifestyles.Tests.dll"
end

task :buildwrap do |dep|
   cmd = Exec.new
	 cmd.command = "o.exe"
	 cmd.parameters = "build-wrap"
   cmd.execute
end

task :publishwrap do |dep|
   cmd = Exec.new
	 cmd.command = "o.exe"
	 cmd.parameters = "publish-wrap -remote local -name Castle.Windsor.Lifestyles"
   cmd.execute
end



