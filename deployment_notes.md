# Deployment Notes 

## Table of Contents

<!-- toc -->

## Deploy multiple sites on digitalocean with nginx server blocks 

- See [this digitalocean tutorial](https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-server-blocks-virtual-hosts-on-ubuntu-16-04).


## Security

### Basic 

- Set up a firewall and only expose ports needed (e.g. port 80/443 and 22 for SSH)
- Disable root logins in your `/etc/ssh/sshd_config`
- Copy over your public keys and disable password logins in `/etc/ssh/sshd_config`

For detailed steps see [python-notes/deployment.md](https://github.com/jessicarush/python-notes/blob/master/deployment.md#ssh).


### Ban repeated login attempts

Fail2Ban is an intrusion prevention software framework that protects computer servers from brute-force attacks. It sets up a daemon that can be used to monitor the logs of services and ban clients that repeatedly fail authentication checks.

You configure the amount of login attempts within a period and the ban length. For example, if more than *x* attempts in *n* minutes, ban the client for *m* minutes.

See this [digitalocean tutorial](https://www.digitalocean.com/community/tutorials/how-to-protect-an-nginx-server-with-fail2ban-on-ubuntu-14-04) for how to set it up.


### Rate Limiting 

Rate limiting is a strategy for limiting network traffic. It puts a cap on how often someone can repeat an action within a certain time frame – for instance, trying to log in to an account. Rate limiting can help stop certain kinds of malicious bot activity. It can also reduce strain on web servers. However, rate limiting is not a complete solution for managing bot activity.

Rate limiting runs within an application, rather than running on the web server itself. Typically, rate limiting is based on tracking the IP addresses that requests are coming from, and tracking how much time elapses between each request.

A rate limiting solution measures the amount of time between each request from each IP address, and also measures the number of requests within a specified time frame. If there are too many requests from a single IP within the given time frame, the rate limiting solution will not fulfill the IP address's requests for a certain amount of time.

The [ngx_http_limit_reg_module](https://nginx.org/en/docs/http/ngx_http_limit_req_module.html) is used to limit the request processing rate per a defined key, in particular, the processing rate of requests coming from a single IP address.

### WAF

A web application firewall (WAF) is a specific form of application firewall that filters, monitors, and blocks HTTP traffic to and from a web service. By inspecting HTTP traffic, it can prevent attacks exploiting a web application's known vulnerabilities, such as SQL injection, cross-site scripting (XSS), file inclusion, and improper system configuration.

[ModSecurity](https://modsecurity.org/) is an open source, cross platform web application firewall (WAF) engine for Apache, IIS and Nginx that is developed by Trustwave's SpiderLabs. That being said, Trustwave has announced:

> Trustwave is announcing the End-of-Life (EOL) of our support for ModSecurity effective July 1, 2024. We will then hand over the maintenance of ModSecurity code back to the open-source community. 

The [project can be found on GitHub here](https://github.com/SpiderLabs/ModSecurity). Hopefully, someone else will pick it up and maintain it.

[OWASP](https://owasp.org/) has created a core rule set for ModSecurity. Tutorials for [setting up ModSecurity and the rule sets can be found here](https://owasp.org/www-project-modsecurity-core-rule-set/).

### Security links 

- [OWASP (Open web application security project)](https://owasp.org/)