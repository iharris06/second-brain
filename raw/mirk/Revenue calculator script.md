<style>

.biz-calc-wrapper {

font-family: system-ui, -apple-system, sans-serif;

max-width: 1024px;

margin: 0 auto;

padding: 20px;

color: #0f172a;

background: #ffffff;

border-radius: 16px;

box-sizing: border-box;

}

.biz-calc-wrapper * {

box-sizing: border-box;

}

.biz-calc-grid {

display: grid;

grid-template-columns: 1fr;

gap: 30px;

}

@media(min-width: 768px) {

.biz-calc-grid {

grid-template-columns: 5fr 7fr;

gap: 40px;

}

}

.biz-calc-card {

background: #f8fafc;

border: 1px solid #e2e8f0;

border-radius: 16px;

padding: 24px;

box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1);

display: flex;

flex-direction: column;

justify-content: center;

}

.biz-calc-input-group {

margin-bottom: 32px;

}

.biz-calc-label-row {

display: flex;

justify-content: space-between;

align-items: center;

margin-bottom: 12px;

}

.biz-calc-label {

font-weight: 600;

display: flex;

align-items: center;

gap: 8px;

font-size: 1rem;

margin: 0;

}

.biz-calc-info-icon {

position: relative;

display: inline-flex;

align-items: center;

cursor: help;

color: #64748b;

}

.biz-calc-tooltip {

visibility: hidden;

opacity: 0;

position: absolute;

bottom: 100%;

left: 50%;

transform: translateX(-50%) translateY(-8px);

background-color: #0f172a;

color: #ffffff;

text-align: center;

padding: 8px 12px;

border-radius: 6px;

font-size: 0.875rem;

font-weight: 400;

white-space: nowrap;

z-index: 10;

transition: opacity 0.2s, transform 0.2s;

pointer-events: none;

box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);

}

.biz-calc-tooltip::after {

content: "";

position: absolute;

top: 100%;

left: 50%;

margin-left: -5px;

border-width: 5px;

border-style: solid;

border-color: #0f172a transparent transparent transparent;

}

.biz-calc-info-icon:hover .biz-calc-tooltip {

visibility: visible;

opacity: 1;

transform: translateX(-50%) translateY(-4px);

}

.biz-calc-badge {

background: rgba(59, 130, 246, 0.1);

color: #3b82f6;

padding: 4px 12px;

border-radius: 6px;

font-weight: 700;

font-size: 1.125rem;

}

.biz-calc-slider {

width: 100%;

accent-color: #3b82f6;

cursor: pointer;

height: 6px;

}

.biz-calc-input {

width: 100%;

padding: 12px 12px 12px 36px;

border: 1px solid #cbd5e1;

border-radius: 8px;

font-size: 1.125rem;

outline: none;

transition: border-color 0.2s;

background: #ffffff;

color: #0f172a;

}

.biz-calc-input:focus {

border-color: #3b82f6;

box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.2);

}

.biz-calc-input-wrapper {

position: relative;

}

.biz-calc-input-icon {

position: absolute;

left: 12px;

top: 50%;

transform: translateY(-50%);

color: #64748b;

}

.biz-calc-range-labels {

display: flex;

justify-content: space-between;

font-size: 0.75rem;

color: #64748b;

margin-top: 8px;

font-weight: 500;

}

.biz-calc-helper-text {

font-size: 0.875rem;

color: #64748b;

margin-top: 8px;

}

.biz-calc-result-card {

background: linear-gradient(135deg, #ffffff, #f8fafc);

border: 1px solid rgba(59, 130, 246, 0.2);

border-radius: 24px;

padding: 40px 24px;

text-align: center;

position: relative;

overflow: hidden;

box-shadow: 0 0 40px rgba(59, 130, 246, 0.15);

height: 100%;

display: flex;

flex-direction: column;

justify-content: center;

}

.biz-calc-icon-down {

background: rgba(239, 68, 68, 0.1);

color: #ef4444;

width: 48px;

height: 48px;

border-radius: 50%;

display: inline-flex;

align-items: center;

justify-content: center;

margin-bottom: 16px;

}

.biz-calc-result-title {

font-size: 1.5rem;

font-weight: 600;

margin: 0 0 8px 0;

color: #0f172a;

}

.biz-calc-huge-number {

font-size: 3.5rem;

font-weight: 800;

background: linear-gradient(to right, #3b82f6, #60a5fa);

-webkit-background-clip: text;

-webkit-text-fill-color: transparent;

margin: 10px 0;

line-height: 1.1;

}

@media(min-width: 768px) {

.biz-calc-huge-number { font-size: 4.5rem; }

}

.biz-calc-result-subtitle {

color: #64748b;

font-weight: 500;

margin: 0 0 32px 0;

}

.biz-calc-stats-grid {

display: grid;

grid-template-columns: 1fr 1fr;

gap: 16px;

border-top: 1px solid #e2e8f0;

padding-top: 32px;

margin-top: auto;

}

.biz-calc-stat-box {

background: #ffffff;

border: 1px solid #e2e8f0;

border-radius: 12px;

padding: 16px;

}

.biz-calc-stat-label {

font-size: 0.875rem;

color: #64748b;

margin: 0 0 4px 0;

}

.biz-calc-stat-value {

font-size: 1.5rem;

font-weight: 700;

margin: 0;

color: #0f172a;

}

</style>

<div class="biz-calc-wrapper">

<div class="biz-calc-grid">

<!-- Left Column: Inputs -->

<div class="biz-calc-card">

<div class="biz-calc-input-group">

<div class="biz-calc-label-row">

<label class="biz-calc-label">

<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#3b82f6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path><line x1="22" y1="2" x2="16" y2="8"></line><line x1="16" y1="2" x2="22" y2="8"></line></svg>

Missed Calls Per Week

</label>

<span class="biz-calc-badge" id="val-calls">20</span>

</div>

<input type="range" id="input-calls" class="biz-calc-slider" min="0" max="300" value="20">

<div class="biz-calc-range-labels">

<span>0</span>

<span>300</span>

</div>

<p class="biz-calc-helper-text">Businesses miss 28%–62%+ of inbound calls (National Average).</p>

</div>

<div class="biz-calc-input-group">

<div class="biz-calc-label-row">

<label class="biz-calc-label">

<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#3b82f6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="1" x2="12" y2="23"></line><path d="M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"></path></svg>

Average Sale Value

</label>

</div>

<div class="biz-calc-input-wrapper">

<svg class="biz-calc-input-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="1" x2="12" y2="23"></line><path d="M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"></path></svg>

<input type="number" id="input-sale" class="biz-calc-input" min="0" max="10000" value="300">

</div>

</div>

<div class="biz-calc-input-group" style="margin-bottom: 0;">

<div class="biz-calc-label-row">

<label class="biz-calc-label">

<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#3b82f6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="19" y1="5" x2="5" y2="19"></line><circle cx="6.5" cy="6.5" r="2.5"></circle><circle cx="17.5" cy="17.5" r="2.5"></circle></svg>

Close Rate

<div class="biz-calc-info-icon">

<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle><line x1="12" y1="16" x2="12" y2="12"></line><line x1="12" y1="8" x2="12.01" y2="8"></line></svg>

<span class="biz-calc-tooltip">The percentage of leads you typically convert into paying customers.</span>

</div>

</label>

<span class="biz-calc-badge" id="val-close">30%</span>

</div>

<input type="range" id="input-close" class="biz-calc-slider" min="1" max="100" value="30">

<div class="biz-calc-range-labels">

<span>1%</span>

<span>100%</span>

</div>

</div>

</div>

<!-- Right Column: Results -->

<div>

<div class="biz-calc-result-card">

<div class="biz-calc-icon-down">

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="22 17 13.5 8.5 8.5 13.5 2 7"></polyline><polyline points="16 17 22 17 22 11"></polyline></svg>

</div>

<h3 class="biz-calc-result-title">Revenue Going to Your Competition</h3>

<div class="biz-calc-huge-number" id="res-yearly">$0</div>

<p class="biz-calc-result-subtitle">Per Year in Missed Calls</p>

<div class="biz-calc-stats-grid">

<div class="biz-calc-stat-box">

<p class="biz-calc-stat-label">Weekly Missed</p>

<p class="biz-calc-stat-value" id="res-weekly">$0</p>

</div>

<div class="biz-calc-stat-box">

<p class="biz-calc-stat-label">Monthly Missed</p>

<p class="biz-calc-stat-value" id="res-monthly">$0</p>

</div>

</div>

</div>

</div>

</div>

</div>

<script>

(function() {

const inputCalls = document.getElementById('input-calls');

const inputSale = document.getElementById('input-sale');

const inputClose = document.getElementById('input-close');

const valCalls = document.getElementById('val-calls');

const valClose = document.getElementById('val-close');

const resYearly = document.getElementById('res-yearly');

const resWeekly = document.getElementById('res-weekly');

const resMonthly = document.getElementById('res-monthly');

const formatCurrency = (value) => {

return new Intl.NumberFormat('en-US', {

style: 'currency',

currency: 'USD',

maximumFractionDigits: 0,

}).format(value);

};

let currentYearly = 0;

let currentWeekly = 0;

let currentMonthly = 0;

const animateValue = (element, start, end, duration) => {

if (start === end) return;

const startTime = [performance.now](http://performance.now/)();

const animate = (currentTime) => {

const elapsed = currentTime - startTime;

const progress = Math.min(elapsed / duration, 1);

const easeProgress = progress === 1 ? 1 : 1 - Math.pow(2, -10 * progress);

const current = start + (end - start) * easeProgress;

element.textContent = formatCurrency(current);

if (progress < 1) {

requestAnimationFrame(animate);

} else {

element.textContent = formatCurrency(end);

}

};

requestAnimationFrame(animate);

};

const calculate = () => {

const calls = parseFloat(inputCalls.value) || 0;

const sale = parseFloat(inputSale.value) || 0;

const close = parseFloat(inputClose.value) || 0;

valCalls.textContent = calls;

valClose.textContent = close + '%';

const targetWeekly = calls _(close / 100)_ sale;

const targetMonthly = targetWeekly * 4.33;

const targetYearly = targetWeekly * 52;

animateValue(resYearly, currentYearly, targetYearly, 500);

animateValue(resWeekly, currentWeekly, targetWeekly, 500);

animateValue(resMonthly, currentMonthly, targetMonthly, 500);

currentYearly = targetYearly;

currentWeekly = targetWeekly;

currentMonthly = targetMonthly;

};

inputCalls.addEventListener('input', calculate);

inputSale.addEventListener('input', calculate);

inputClose.addEventListener('input', calculate);

// Run once on load

calculate();

})();

</script>