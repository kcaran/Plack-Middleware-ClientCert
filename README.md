# NAME

Plack::Middleware::ClientCert - Parse digital client certificates for Perl's PSGI web servers.

# VERSION

version 0.01

# SYNOPSIS

Parse a client certificate and put details in the env

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

client\_cn
client\_ou
client\_o

# NAME

Plack::Middleware::ClientCert

# AUTHOR

Keith Carangelo <mail@kcaran.com>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2016 by Keith Carangelo.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
