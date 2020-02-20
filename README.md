# Jelly Adventures in FreeBSD

## Install required packages

    pkg install ca_root_nss libunwind icu openssl

## Download/install dotnet package

    mkdir /dotnet
    cd /dotnet
    fetch https://dotnetcli.blob.core.windows.net/dotnet/Sdk/master/dotnet-sdk-latest-freebsd-x64.tar.gz
    tar -xf dotnet-sdk-latest-freebsd-x64.tar.gz

## Download jellyfin

    mkdir /jellyfin
    cd /jellyfin
    fetch https://repo.jellyfin.org/releases/server/portable/nightly/jellyfin-nightly_20200220.tar.gz
    tar -xf jellyfin-nightly_20200220.tar.gz
    cd jellyfin_10.5.0

## Symlink openssl and crypto libraries to the expected place for dotnet

    ln -s /usr/local/lib/libssl.so /usr/local/lib/libssl.so.8
    ln -s /usr/local/lib/libcrypto.so /usr/local/lib/libcrypto.so.8

## Run Jellyfin

    /dotnet/dotnet jellyfin

## Failure

    ld-elf.so.1: /dotnet/shared/Microsoft.NETCore.App/3.0.0-preview-27218-01/System.Security.Cryptography.Native.OpenSsl.so: Undefined symbol "CRYPTO_num_locks"
