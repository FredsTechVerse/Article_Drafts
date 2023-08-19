### USING CHART JS

- With multiple datasets , we can have multiple charts in one chart eg With the three datasets , we have 3 charts inside one chart with additional props to define how things will look.

- Here are the steps to integrate charts easily :-

1. Install the react-chartjs-2 package `yarn add chart.js react-chartjs-2`

2. Import crucial elements from chart.js via `import { Doughnut } from "react-chartjs-2";`

3. Import the chart we wanna use from react-chartjs-2 via `import { Doughnut } from "react-chartjs-2";`
4. Register the visitors with `ChartJS.register(ArcElement, Tooltip, Legend);`

5. We are set to go `<Doughnut data={chartJsData} options={options}  />`

- Use the sandbox to fetch any chart source code that you would like to use eg
  [LineChart](https://codesandbox.io/s/github/reactchartjs/react-chartjs-2/tree/master/sandboxes/line/default?from-embed=&file=/App.tsx:36-148)

  - [DoughnutChart](https://codesandbox.io/s/github/reactchartjs/react-chartjs-2/tree/master/sandboxes/doughnut/default?from-embed=&file=/App.tsx:217-242)
  - [BarChart]{https://codesandbox.io/s/github/reactchartjs/react-chartjs-2/tree/master/sandboxes/bar/vertical?from-embed=&file=/App.tsx:613-975}

  - The area chart differs from the line chart in that it has a filler component.

- Here is an example of the options and chartData objects that you will ever need :-

```js
  const options = {
  borderRadius: 10,
  borderWidth: 1,
  spacing: 5,
  circumference: 360, // We can define a semicircle by using 180 etc .
  cutout: "70%", //The gist of the doughnut which defines the holloness of the piechart
  animation: { animateScale: true, animateRotate: true },

    plugins: {
        title: { display: true, text: "Distribution of Users" }, =>
        legend: { display: false },
      },

};

const chartData = {
labels: ["Tutors", "Students", "Admin"],
datasets: [
{
label: "Poll",
data: [24, 3, 36],
backgroundColor: ["red", "green", "blue"],
borderColor: ["red", "green", "blue"],
},
{
label: "Poll",
data: [40, 30, 80],
backgroundColor: ["gray", "orange", "pink"],
borderColor: ["red", "green", "blue"],
},
{
label: "Poll",
data: [24, 72, 45],
backgroundColor: ["gray", "orange", "pink"],
borderColor: ["red", "green", "blue"],
},
],
};
```

- Speaking of options , those that need embedding are well defined eg `animation.animateScale` and `animation.animateRotate`

