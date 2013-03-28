# CAS plugin for Nagios

Nagios plugin to check CAS authentication

## Usage
```
NAME
      check-cas.pl - Nagios CAS (Central authentication Service) check plugins.

DESCRIPTION
      Nagios CAS (Central authentication Service) check plugins. First it does
    a request to get the CAS Login Ticket (lt) and the CAS Cookie from the login
    page. Then it does a request to authenticate with the Login ticket, the
    cookie, the username and the password. No support for http redirection in
    request, login page and authentication page must be directly accessible. if
    exists, it also retreive performance data for nagios.

SYNOPSIS
      check-cas.pl [--version] [--help] [--verbose <level>] [--debug <level>]
                   [--timeout <threshold> ] --hostname <host> [--port <port>]
                   [--url <URL>] [--ltregex <regex>] --login <username>
                   --authentication <password> --regex <regex>
                   [--npd-url <nagios performance data url>]
                   [--npd-regex <nagios performance data regex>]

      Options:
       --version      : Display plugins version.
       --help         : Display this help.
       --verbose      : Same as debug option (0-9).
       --debug        : Increase debug (0-9).
       --timeout      : Time threshold to wait before timeout (in second).

       --hostname     : The CAS server host <name or IP).
       --port         : The CAS server port.
       --url          : The CAS server login URL.
       --ltregex      : Regex to find the CAS login token.

       --login        : The username used to authenticate.
       --authenticate : The password for the user to authenticate.
       --regex        : The matching regex to validate a success.
       --npd-url      : The url where to find nagios performance data.
       --npd-regex    : Regex matching the nagios performance data.

OPTIONS
    --version
         Display plugins version.

    --help
         Display this help.

    --verbose [0-9]
         Same as debug option.

    --debug [0-9]
         Define a debug level between 0 and 9. 0 means no debug and 9 means
         full debug (default to 0).

    --timeout
         Time threshold in second to wait before timeout (default to 30).

    --hostname <host>
         The CAS server host. It can be a DNS name or an IP address.

    --port <port
         The CAS server port (default to 80).

    --url <URL
         The CAS server login URL (default to "/cas/login").

    --ltregex <regex
         Regex to find the CAS login token (default to "input type="hidden"
         name="lt" value="([-a-zA-Z0-9_]+)").

    --login <username
         The username used to authenticate.

    --authenticate <password>
         The password for the user to authenticate.

    --regex <regex>
         The matching regex to validate a success.

    --npd-url <nagios performance data url
         The url where to find nagios performance data. (default to
         "/cas/services/viewStatistics.html").

    --npd-regex <nagios performance data regex
         Regex matching the nagios performance data. (default to
         "<nagiosPerformanceData>(.*)</nagiosPerformanceData>").

EXAMPLES
      Using check_cas.pl script:
    perl check_cas.pl -H cas.example.fr -u "/cas/login" -p 443
    -l username -a password -r "Log In Successful"
