# Jelly Adventures in FreeBSD

## Getting Started

If using vagrant:

    vagrant up jellyfin
    vagrant ssh jellyfin

Otherwise, a fresh FreeBSD 12.1-RELEASE server to dev on

## Configuring the Server

### Install required packages

    pkg install ca_root_nss libunwind icu libressl

### Download/install dotnet package

    mkdir /dotnet
    cd /dotnet
    fetch https://dotnetcli.blob.core.windows.net/dotnet/Sdk/master/dotnet-sdk-latest-freebsd-x64.tar.gz
    tar -xf dotnet-sdk-latest-freebsd-x64.tar.gz

### Download jellyfin

    mkdir /jellyfin
    cd /jellyfin
    fetch https://repo.jellyfin.org/releases/server/portable/stable/jellyfin_10.5.0.portable.tar.gz
    tar -xf jellyfin_10.5.0.portable.tar.gz
    cd jellyfin_10.5.0

### Symlink openssl and crypto libraries to the expected place for dotnet

    ln -s /usr/local/lib/libssl.so /usr/local/lib/libssl.so.8
    ln -s /usr/local/lib/libcrypto.so /usr/local/lib/libcrypto.so.8

### Run Jellyfin

    /dotnet/dotnet -d jellyfin

## Failure

# /dotnet/dotnet -d jellyfin

    Telemetry is: Enabled
    projectfactory: MSBUILD_EXE_PATH = /dotnet/sdk/3.0.100-preview-010021/MSBuild.dll
    projectfactory: MSBuild project path =
    projecttoolscommandresolver: ProjectFactory did not find Project.
    Microsoft.DotNet.Cli.Utils.CommandUnknownException: No executable found matching command "dotnet-jellyfin". See https://aka.ms/missing-command for more information.
       at Microsoft.DotNet.CommandFactory.CommandFactoryUsingResolver.Create(ICommandResolverPolicy commandResolverPolicy, String commandName, IEnumerable`1 args, NuGetFramework framework, String configuration, String outputPath, String applicationName)
       at Microsoft.DotNet.CommandFactory.CommandFactoryUsingResolver.Create(String commandName, IEnumerable`1 args, NuGetFramework framework, String configuration, String outputPath, String applicationName)
       at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
       at Microsoft.DotNet.Cli.Program.Main(String[] args)
