jquery-ui-intervals
===================

Extends jquery-ui slider widget to include multiple ranges within a single slider

Live example at jsFiddle http://jsfiddle.net/ladrower/BmQq4/


Intervals class constructor
===========================
**Intervals**
```javascript
/**
 * @class Intervals
 * @constructor
 * @param {String} selector jQuery selector
 * @param {Object} userOptions (optional) Custom options object that overrides default
 * {
 *      @property {Number} userOptions.min Slider minimum value
 *      @property {Number} userOptions.max Slider maximum value
 *      @property {Number} userOptions.step Slider sliding step
 *      @property {Number} userOptions.gap Minimum gap between handles when add/remove range controls are visible
 *      @property {Number} userOptions.newlength Default length for newly created range. Will be adjusted between surrounding handles if not fitted
 *      @property {Boolean} userOptions.disabled Slider disability flag
 * }
 */

window.Intervals = function(selector, userOptions) {}
```


Intervals class interface
=========================

**addPeriod**
```javascript
/**
 * Adds single period to this intervals instance and rebuilds the slider
 * @param {Number} start - start point for the period
 * @param {Number} length - the length for the period
 * @return {Object|null}
 */

Intervals.addPeriod = function(start, length) {}
```

=
**addPeriods**
```javascript
/**
 * Adds multiple periods and rebuilds the intervals slider
 * @param {Array} periodsArray example: Array([[0,20],[40,60]...])
 * @return {Object} self instance of am.Intervals class
 */

Intervals.addPeriods = function(periodsArray) {}
```

=
**getPeriod**
```javascript
/**
 * Get period by id
 * @param {Number} id
 * @return {Object}
 */

Intervals.getPeriod = function(id) {}
```

=
**getPeriods**
```javascript
/**
 * Gets all periods for this intervals instance
 * @return {Array} of each period.toPublic() object
 */

Intervals.getPeriods = function() {}
```

=
**isValidPeriod**
```javascript
/**
 * @param {Number} id - period Id
 * @param {Array[Number, Number]} abscissas as [a1, a2]
 * @return {Boolean}
 */

Intervals.isValidPeriod = function(id, abscissas) {}
```

=
**updatePeriod**
```javascript
/**
 * @param {Number} id - period Id
 * @param {Array} abscissas as [a1, a2]
 * @return {Object} self instance of Intervals class
 */

Intervals.updatePeriod = function(id, abscissas) {}
```

=
**setDeletePeriodConfirmCallback**
```javascript
/**
 * Sets callback function that can be used for period delete confirmation window
 *
 * @param {Function} confirmFunction
 *      stores a callback function
 *      function args:
 *          1. period - instance of current period.toPublic() object to be passed to confirmation window
 *          2. callback result flag of boolean
 *
 * @example
 *      intervals.setDeletePeriodConfirmCallback(function(period, callback) {
 *          callback(function() {
 *             return confirm('Delete period between ' + period.getAbscissas()[0] + ' and ' + period.getAbscissas()[1] + ' ?');
 *          }());
 *      });
 * @return {Object} self instance of Intervals class
 */

Intervals.setDeletePeriodConfirmCallback = function(confirmFunction) {}
```

=
**setAddPeriodConfirmCallback**
```javascript
/**
 * Sets callback function that can be used for period add confirmation window
 *
 * @param {Function} confirmFunction
 *      stores a callback function
 *      function args:
 *          1. period - instance of new period.toPublic() object that can be confirmed or rejected
 *          2. callback result flag of boolean
 *
 * @example
 *      intervals.setAddPeriodConfirmCallback(function(period, callback) {
 *          callback(function() {
 *             return confirm('Add period between ' + period.getAbscissas()[0] + ' and ' + period.getAbscissas()[1] + ' ?');
 *          }());
 *      });
 * @return {Object} self instance of Intervals class
 */

Intervals.setAddPeriodConfirmCallback = function(confirmFunction) {}
```

=
**setOnHandleMouseenterCallback**
```javascript
/**
 * Sets callback function for handle's mouseenter event
 *
 * @param {Function} callbackFunction
 *      stores a callback function
 *      function args:
 *          1. context - jQuery object of hovered handle
 *          2. period - instance of period.toPublic() object that is linked to hovered handle
 *          3. edgeIndex - integer number[0-1] indicating left or right handle triggered
 *
 * @example
 *      intervals.setOnHandleMouseenterCallback(function(context, period, edgeIndex) {
 *          var handlePosition = context.offset().left;
 *          var periodId = period.getId();
 *          var handleAbscissa = period.getAbscissas()[edgeIndex];
 *          //...
 *      });
 * @return {Object} self instance of Intervals class
 */

Intervals.setOnHandleMouseenterCallback = function(callbackFunction) {}
```

=
**setOnHandleSlideCallback**
```javascript
/**
 * Sets callback function for handle's slide event
 *
 * @param {Function} callbackFunction
 *      stores a callback function
 *      function args:
 *          1. context - jQuery object of slided handle
 *          2. period - instance of period.toPublic() object that is linked to slided handle
 *          3. edgeIndex - integer number[0-1] indicating left or right handle triggered
 *
 * @example
 *      intervals.setOnHandleSlideCallback(function(context, period, edgeIndex) {
 *          var handlePosition = context.offset().left;
 *          var periodId = period.getId();
 *          var handleAbscissa = period.getAbscissas()[edgeIndex];
 *          //...
 *      });
 * @return {Object} self instance of Intervals class
 */

Intervals.setOnHandleSlideCallback = function(callbackFunction) {}
```

=
**setOnBeforeHandleSlideCallback**
```javascript
/**
 * Sets callback function for handle's before slide event
 * Prevents slide if callback function returns `false`
 *
 * @param {Function} callbackFunction
 *      stores a callback function
 *      function args:
 *          1. context - jQuery object of slided handle
 *          2. period - instance of period.toPublic() object that is linked to slided handle
 *          3. edgeIndex - integer number[0-1] indicating left or right handle triggered
 *
 * @example
 *      intervals.setOnHandleSlideCallback(function(context, period, edgeIndex) {
 *          var handlePosition = context.offset().left;
 *          var periodId = period.getId();
 *          var handleAbscissa = period.getAbscissas()[edgeIndex];
 *
 *          if (handleAbscissa > 50) {
 *              return false;
 *          }
 *          //...
 *      });
 * @return {Object} self instance of Intervals class
 */

Intervals.setOnBeforeHandleSlideCallback = function(callbackFunction) {}
```

=
**empty**
```javascript
/**
 * Deletes all periods and rebuilds the intervals slider
 * @return {Object} self instance of Intervals class
 */

Intervals.empty = function() {}
```

=
**getSlider**
```javascript
/**
 * Gets jQuery object associated with this intervals instance
 * @return {Object} jQuery object
 */

Intervals.getSlider = function() {}
```

=
**isDestroyed**
```javascript
/**
 * Checks if slider DOM element has been unwidgetized
 * @return {Boolean}
 */

Intervals.isDestroyed = function() {}
```

=
**isDisabled**
```javascript
/**
 * Checks if slider is disabled
 * @return {Boolean}
 */

Intervals.isDisabled = function() {}
```

=
**enable**
```javascript
/**
 * Enables slider
 * @return {Object} self instance of Intervals class
 */

Intervals.enable = function() {}
```

=
**disable**
```javascript
/**
 * Disables slider for user manipulations
 * @return {Object} self instance of Intervals class
 */

Intervals.disable = function() {}
```

=========================




