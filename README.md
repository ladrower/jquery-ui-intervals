jquery-ui-intervals
==================

Extends jquery-ui slider widget to include multiple ranges within a single slider

Live example at jsFiddle http://jsfiddle.net/3kZTe/5/


Intervals class interface
=========================


/**
 * Adds single period to this intervals instance and rebuilds the slider
 * @param {Number} start - start point for the period
 * @param {Number} length - the length for the period
 * @return {Object|null}
 * 
 */

Intervals.addPeriod = function(start, length) {}


=
/**
 * Adds multiple periods and rebuilds the intervals slider
 * @param {Array} periodsArray example: Array([[0,20],[40,60]...])
 * @return {Object} self instance of am.Intervals class
 * 
 */

Intervals.addPeriods = function(periodsArray) {}


=
/**
 * Get period by id
 * @param {Number} id
 * @return {Object}
 * 
 */

Intervals.getPeriod = function(id) {}


=
/**
 * Gets all periods for this intervals instance
 * @return {Array} of each period.toPublic() object
 * 
 */

Intervals.getPeriods = function() {}


=
/**
 * @param {Number} id - period Id
 * @param {Array[Number, Number]} abscissas as [a1, a2]
 * @return {Boolean}
 * 
 */

Intervals.isValidPeriod = function(id, abscissas) {}


=
/**
 * @param {Number} id - period Id
 * @param {Array} abscissas as [a1, a2]
 * @return {Object} self instance of Intervals class
 * 
 */

Intervals.updatePeriod = function(id, abscissas) {}


=
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
 * 
 */

Intervals.setDeletePeriodConfirmCallback = function(confirmFunction) {}


=
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
 * 
 */

Intervals.setAddPeriodConfirmCallback = function(confirmFunction) {}


=
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
 * 
 */

Intervals.setOnHandleMouseenterCallback = function(callbackFunction) {}


=
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
 * 
 */

Intervals.setOnHandleSlideCallback = function(callbackFunction) {}


=
/**
 * Deletes all periods and rebuilds the intervals slider
 * @return {Object} self instance of Intervals class
 * 
 */

Intervals.empty = function() {}


=
/**
 * Gets jQuery object associated with this intervals instance
 * @return {Object} jQuery object
 * 
 */

Intervals.getSlider = function() {}


=
/**
 * Checks if slider DOM element has been unwidgetized
 * @return {Boolean}
 * 
 */

Intervals.isDestroyed = function() {}


=========================




