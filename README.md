## Overview

This is a small CGI program that returns the output of [mtr][m] (a ping /
traceroute hybrid) from the web server back to the HTTP client, or to another
host as guided by the `target` query parameter.

I use it to to attach connectivity reports to monitoring alerts triggered by
packet loss.

It includes some simple locking and paranoia to avoid basic abuse, but probably
isn't bulletproof.

## Usage

* curl https://example.com/maas
* curl https://example.com/maas?target=8.8.8.8
* curl https://example.com/maas?target=8.8.8.8&cycles=5

## Example output
        HOST: example.com                                       Loss%   Snt   Last   Avg  Best  Wrst StDev
          1.|-- 11-11-11-1.no-reverse-dns-set.example.com        0.0%     5    0.2   0.4   0.2   0.5   0.1
          2.|-- 1-111-111-111.no-reverse-dns-set.example.com     0.0%     5    0.8   0.8   0.7   1.0   0.1
          3.|-- po1.cr1.zzz.example.com                          0.0%     5    1.0   4.5   0.8  19.0   8.1
          4.|-- po3.cr2.zzz.example.com                          0.0%     5    0.9   0.8   0.7   0.9   0.1
          5.|-- te0-0-2-2.zzz.lon.example.com                    0.0%     5    8.5   7.1   6.1   8.5   1.2
          6.|-- google1.lonap.net                                0.0%     5    6.7   6.1   5.9   6.7   0.3
          7.|-- 216.239.47.221                                   0.0%     5    6.7   6.8   6.7   6.9   0.1
          8.|-- 216.239.47.53                                    0.0%     5    6.8   6.7   6.6   6.8   0.1
          9.|-- google-public-dns-a.google.com                   0.0%     5    6.5   6.6   6.5   6.7   0.1

## License

Released under [ASL][a]. See LICENSE for details and (no) warranty.

## Author

Jon Stuart, jon@zomo.co.uk, [Zomo Technology Ltd][z], 2014.

[a]: http://www.opensource.org/licenses/Apache-2.0
[m]: http://www.bitwizard.nl/mtr/
[z]: http://www.zomo.co.uk
