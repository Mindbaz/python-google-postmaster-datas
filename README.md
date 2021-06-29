# Google Postmaster Datas

Unofficial tool to download and flatten data from GPT. The recovered data will
offer a simple schema in order to be able to easily save this data in a flat
file or in database.

## Schema

* user_report_spam_percent : `float|None`
* ips_reputations : `list`
* domain_reputation : `level|None`
* feedback_loop : `{ nb_campaigns: 0, percent_per_campaign: list }`
* auth_use_dkim_percent : `float|None`
* auth_use_spf_percent : `float|None`
* auth_use_dmarc_percent : `float|None`
* tls_inbound_percent : `float|None`
* delivery_errors : `list`
* domain : `str`
* date : `str`

### Level

Translates string level from GTP to int

| EN     | FR              | int |
|:------:|:---------------:|:---:|
| high   | bonne           | 4   |
| medium | moyenne         | 3   |
| low    | plutôt mauvaise | 2   |
| bad    | mauvaise        | 1   |
| unknow | unknow          | 0   |
  
### ips_reputations
  
    [ { 'level': level, 'value': float, 'ips': str } ]

### feedback_loop

    percent_per_campaign : [ { 'uid': int, 'spam_percent': float } ]

# How to use it

    $ python entry_points_googlepostmasterapi/gpt_dl_all_datas.py -h
    
    usage: gpt_dl_all_datas [-h] [--token [TOKEN]] [--pool-size [POOL_SIZE]]
                            [--date [DATE]] [--verbose] [--version]

    arguments:
      -h, --help            show this help message and exit
      --token [TOKEN]       GPT token
      --pool-size [POOL_SIZE]
                            Number of parallel calls to GPT. Default : 2
      --date [DATE]         Date to fetch datas from GPT. Format : YYYY-MM-DD.
                            Default : D-2
      --verbose             Verbose mode
      --version             Display version


    $ python entry_points_googlepostmasterapi/gpt_dl_domain_datas.py -h
    usage: gpt_dl_domain_datas [-h] [--token [TOKEN]] [--domain [DOMAIN]]
                               [--date [DATE]] [--verbose] [--version]
    
    arguments:
      -h, --help         show this help message and exit
      --token [TOKEN]    GPT token
      --domain [DOMAIN]  Domain
      --date [DATE]      Date to fetch datas from GPT. Format : YYYY-MM-DD.
                         Default : D-2
      --verbose          Verbose mode
      --version          Display version

# Support version

Python : `>=3.6`
