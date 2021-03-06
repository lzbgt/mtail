<img src="https://raw.githubusercontent.com/google/mtail/master/logo.png" alt="mtail" title="mtail" align="right" width="140">

# mtail - extract whitebox monitoring data from application logs for collection into a timeseries database

[![GoDoc](https://godoc.org/github.com/google/mtail?status.png)](http://godoc.org/github.com/google/mtail)
[![Travis Build Status](https://travis-ci.org/google/mtail.svg)](https://travis-ci.org/google/mtail)
[![CircleCI Build Status](https://circleci.com/gh/google/mtail.svg?style=shield&circle-token=:circle-token)](https://circleci.com/gh/google/mtail)
[![Coverage Status](https://coveralls.io/repos/github/google/mtail/badge.svg?branch=master)](https://coveralls.io/github/google/mtail?branch=master)

`mtail` is a tool for extracting metrics from application logs to be exported
into a timeseries database or timeseries calculator for alerting and
dashboarding.

It aims to fill a niche between applications that do not export their own
internal state, and existing monitoring systems, without patching those
applications or rewriting the same framework for custom extraction glue code.

The extraction is controlled by [mtail programs](docs/Programming-Guide.md)
which define patterns and actions:

    # simple line counter
    counter line_count
    /$/ {
      line_count++
    }

Metrics are exported for scraping by a collector as JSON or Prometheus format
over HTTP, or can be periodically sent to a collectd, StatsD, or Graphite
collector socket.

Read the [programming guide](docs/Programming-Guide.md) if you want to learn how
to write mtail programs.

Mailing list: https://groups.google.com/forum/#!forum/mtail-users

### Installation

`mtail` uses a Makefile. To build `mtail`, type `make` at the commandline. See
the [Build instructions](docs/Building.md) for more details.

### Deployment

`mtail` works best when it paired with a timeseries-based calculator and
alerting tool, like [Prometheus](http://prometheus.io).

> So what you do is you take the metrics from the log files and
> you bring them down to the monitoring system?

[It deals with the instrumentation so the engineers don't have
to!](http://www.imdb.com/title/tt0151804/quotes/qt0386890)  It has the
extraction skills!  It is good at dealing with log files!!
