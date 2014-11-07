# abbajs
[![CI Status](http://img.shields.io/travis/thii/abbajs.svg?style=flat)](https://travis-ci.org/thii/abbajs)
[![Coverage Status](http://img.shields.io/coveralls/thii/abbajs.svg?style=flat)](https://coveralls.io/r/thii/abbajs)
[![Version](http://img.shields.io/npm/v/abbajs.svg?style=flat)](https://www.npmjs.org/package/abbajs)
[![License](http://img.shields.io/npm/l/abbajs.svg?style=flat)](http://opensource.org/licenses/BSD-3-Clause)

A/B test analysis library in JavaScript

## Table of Contents

* [Installation](#installation)
* [Usage](#usage)
  * [Normal Distribution](#normal-distribution)
    * [Density](#density)
    * [CDF](#cdf)
    * [Survival function](#survival-function)
    * [Inverse CDF](#inverse-cdf)
    * [Inverse survival function](#inverse-survival-function)
  * [Binomial Distribution](#binomial-distribution)
    * [Mass function](#mass-function)
    * [CDF](#cdf-1)
    * [Survival function](#survival-function-1)
    * [Inverse CDF](#inverse-cdf-1)
    * [Inverse survival function](#inverse-survival-function-1)
  * [Computes Experiment](#computes-experiment)
* [Running Tests](#running-tests)
* [License](#license)


## Installation

As a Node.js module

```bash
$ npm install abbajs
```

As a component

```bash
$ component install thii/abbajs
```

## Usage

### Normal Distribution
Create a normal distribution analysis with `Abba.NormalDistribution(mean, standardDeviation)`. Available functions are listed below.

#### Density
```javascript
var normal = new Abba.NormalDistribution(1, 2);
var result = normal.density(1);
// 0.19947114020071632
```

#### CDF
```javascript
var normal = new Abba.NormalDistribution(1, 2);
var result = normal.cdf(3);
// 0.8413447460685429
```

#### Survival function
```javascript
var normal = new Abba.NormalDistribution(1, 2);
var result = normal.survival(5);
// 0.02275013194817921
```

#### Inverse CDF
```javascript
var normal = new Abba.NormalDistribution(1, 2);
var result = normal.inverseCdf(0.95);
// 4.289707253902945
```

#### Inverse survival function
```javascript
var normal = new Abba.NormalDistribution(1, 2);
var result = normal.inverseCdf(0.75);
// 2.3489795003921636
```

### Binomial Distribution
Create a binomial distribution analysis with `Abba.BinomialDistribution(numTrials, probability)`. Available functions are listed below.

#### Mass function
```javascript
var binomial = new Abba.BinomialDistribution(1000, 0.3);
var result = binomial.mass(300);
// 0.0275296327870529
```

#### CDF
```javascript
var binomial = new Abba.BinomialDistribution(1000, 0.3);
var result = binomial.cdf(310);
// 0.7656417087768965
```

#### Survival function
```javascript
var binomial = new Abba.BinomialDistribution(1000, 0.3);
var result = binomial.survival(340);
// 0.002596868572741773
```

#### Inverse CDF
```javascript
var binomial = new Abba.BinomialDistribution(1000, 0.3);
var result = binomial.inverseCdf(0.5);
// 300
```

#### Inverse survival function
```javascript
var binomial = new Abba.BinomialDistribution(1000, 0.3);
var result = binomial.inverseSurvival(0.75);
// 290.22571491846537
```

### Computes Experiment
Create an experiment with `Abba.Experiment(numVariations, baselineNumSuccesses, baselineNumTrials, intervalAlpha)`. Get the result of a specific test with `experiment.getResults(numSuccesses, numTrials)`

```javascript
var experiment = new Abba.Experiment(3, 20, 100, 0.05);
var result = experiment.getResults(50, 150);
/* 
{ proportion:
  { value: 0.3333333333333333,
    lowerBound: 0.24862657323794302,
    upperBound: 0.4303072595809455 
  },
  relativeImprovement:
  { value: 0.6666666666666665,
    lowerBound: -0.040933756155489553,
    upperBound: 1.1803459277365715 
  },
  pValue: 0.05749442762442982 
}
*/
```

## Running Tests
```bash
npm install
npm test
```

## License
[BSD-3 Clause](https://raw.githubusercontent.com/thii/abbajs/master/LICENSE)
