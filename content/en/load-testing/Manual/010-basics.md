---
title: "Basics"

weight: 10
type: docs

description: >
  What XLT can do for you, and what you need to start developing and running a load test suite.
---

## What is XLT?
XLT, the Xceptance Load Test tool, is a regression and performance testing tool. The first prototype was released in 2005 and it has been improving ever since. The tool is used on a daily basis at [Xceptance](https://xceptance.com), so our developers know what our load testers need.

XLT is platform independent (you can develop and run your tests on any platform with a JDK), and is open source, available under Apache License 2.0 starting February 2020. It is simple to deploy and highly scalable, provides ready to use reports (for single or multiple test runs, so you can also compare runs or see trends) and realtime test monitoring. Nothing about XLT is proprietary, no custom IDE is needed, you can just use your tool chain and existing knowledge.

## How does it work?
To use XLT, you will model the user actions you expect on your application as a set of JUnit tests, which you can develop and check on your own machine, in your preferred IDE (see [Workflow]({{< relref "050-workflow" >}}) for details how one usually does this), using XLT libraries or even starting out with one of our [sample test suites]({{< relref "/load-testing/test-suites" >}}). To consolidate your test cases, XLT builds a [result browser]({{< relref "440-result-browser" >}}) for every test run (no matter whether it was run from your IDE or in a load test environment) which gives you further insights into what happened, on top of all the info that is put to the console or logs. 

Load testing means firing the tests from your test suite at your application, with many virtual users executing many tests at the same time (XLT allows you to [easily configure]({{< relref "470-load-configuration" >}}) the exact load). So to run a load test, usually a distributed load generation environment made up of a cluster of test machines is required to generate enough load (XLT ships with tools to set up your cluster using [Google Cloud]({{< relref "../advanced/060-cloud-setup#google-cloud-gc" >}}) or [Amazon Web Services]({{< relref "../advanced/060-cloud-setup#amazon-web-services-aws" >}})).

The result of your load test is neatly summed up in a [test report]({{< relref "530-reports" >}}), which may also contain links to the result browsers of single tests within this load test run (e.g. when something went wrong, so you can check the cause for any error). 

## Load Test Components

This is a rough overview of the components:

{{< image src="user-manual/suite-controller-agents.png" >}}
High Level Overview
{{< /image >}}
{{< TODO comment="Better and more stylish image... work in progress?" / >}}

### Test Suite
A test suite contains your test code, data and configuration. Developed on your own machine, it can live in your favorite version control tool and be shared easily.

### MC/Master Controller
The MC can be seen as the “brain” of the load test environment. It deploys the test suite to all load machines, evenly distributes the load, starts/stops the load test and can be used to get agent information and create test reports. A test cluster may only have one master controller. It is loosely coupled so you can (re-)attach to running tests in case you need to interact with them.

### AC/Agent Controller
The MC communicates with the AC. The AC waits, receives and distributes the workload. There is usually one AC per hardware box (but more are possible), which listens typically on port 8500. The AC spawns the test agents. All agents are started and stopped by the AC. ACs are not aware of other ACs; they function independantly and do not interact with one another.

### Agents
The agents are the workhorses of the load test since they actually execute the test suite against the system under test. Basically, an agent is a JVM that runs the users, and each user is a thread with subthreads (inactive threads are possible). The MC is responsible for calculating the user distribution across the agents, but still the agents are a component to watch, as memory tuning and sizing (total and in relation to the box) is important for good and consistent test results. Still, a stalled agent does not block other agents.

### Grafana
Graphite/Grafana can be used to display realtime test information. It shows response times, errors, machine utilization, transaction and action runtimes and can also be paired with infrastructure monitoring. For more details, see [Real-Time Reporting with Graphite]({{< relref "../advanced/100-real-time-monitoring" >}}).

## How to start using XLT

### What to think about
The goal of your load test should be to mimic the expected traffic on your application as accurately as possible. Therefore, you should know the typical scenarios for a user of your application. For example, if you want to test your web shop, these scenarios might be: users just visit the homepage and disappear, users browse or search products but never order, users make an order either as a guest or as a registered user. We built some [sample test suites]({{< relref "/load-testing/test-suites" >}}) with what we think might be plausible test cases, so feel free to have a look.

Also your test environment should mimic the app as accurately as possible. You can test on live systems, but be aware that the load might be too much for your system (after all, you are testing to find out just that). Also, think about the processes that might be triggered by the tests (you don't want to deal with thousands of fake test orders, and your payment provider doesn't want to, either).

While you develop your test cases, the app you want to test should be in a stable state. It's no use writing tests that mimic user requests that will be changed the next day, so first finish your app, then finish your tests.

### What to install
To run XLT, you will need the following:
* latest JDK 8 (or 11)
* Java IDE of choice
* Latest [Apache Ant](https://ant.apache.org/)
* [Maven](https://maven.apache.org/)

Installing XLT is described in more detail [here]({{< relref "040-installation" >}}).

### How to proceed
The [Quick Start]({{< relref "../quick-start" >}}) section offers some guidance on how to start using XLT, from installation to your first local load test. For further info you might want to return to this [User Manual]({{< relref "050-workflow" >}}), where you can learn all the details about developing and configuring your tests, setting up remote machines to generate the load and everything in between. Happy testing!
