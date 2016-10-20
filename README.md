# NAME

Plack::Middleware::ClientCert - Parse a client certificate and put details in the env

# SYNOPSIS

    use Plack::Builder;

    my $app = sub {
        my $env = shift;
        return [
            200,
            [ 'Content-Type' => 'text/plain' ],
            [ "Hello $env->{ client_cn } from $env->{ client_ou } of $env->{ clent_o }" ],
        ];
    };

    builder {
        enable 'ClientCert';
        $app;
    };

# DESCRIPTION

Plack::Middleware::ClientCert parses the fields of a digital certificate
in either Apache or IIS. The certificate distinguished name is either
slash-delimited or comma delimited in the form:

C=US, O=Agents Virtual Community, OU="My Insurance, Inc.", CN=Troy O'Leary

Any fields containing a comma are double-quoted.

The keys for the certificate are:

client_cn
client_ou
client_o

# BUGS

All complex software has bugs lurking in it, and this module is no
exception. If you find a bug please either email me, or add the bug
to cpan-RT.

# AUTHOR

Keith Carangelo <kcaran@gmail.com>

# COPYRIGHT AND LICENSE

Copyright 2016 Keith Carangelo

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.
