<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-md-8">
          <card class="strpied-tabled-with-hover"
                body-classes="table-full-width table-responsive"
          >
            <div id="chart">
              <apex-chart type="bar" height="350" :options="chartOptions" :series="series"></apex-chart>
            </div>
          </card>
        </div>
        <div class="col-md-4">
          <card class="strpied-tabled-with-hover"
                body-classes="table-full-width table-responsive"
          >
            <div id="chart">
              <apex-chart type="donut" :options="chartOptions2" :series="series2"></apex-chart>
            </div>
          </card>
        </div>
        <div class="col-md-12">
          <card class="strpied-tabled-with-hover"
                body-classes="table-full-width table-responsive"
          >
            <div id="chart">
              <apex-chart type="line" height="350" :options="chartOptions3" :series="series3"></apex-chart>
            </div>
          </card>
        </div>
        <div class="col-md-12">
          <card class="strpied-tabled-with-hover"
                body-classes="table-full-width table-responsive"
          >
            <div id="chart">
              <apex-chart type="bar" height="350" :options="chartOptions4" :series="series4"></apex-chart>
            </div>
          </card>
        </div>
        <div class="col-12">
          <card class="strpied-tabled-with-hover"
                body-classes="table-full-width table-responsive"
          >
            <template slot="header">
              <h4 class="card-title">Striped Table with Hover</h4>
              <p class="card-category">Here is a subtitle for this table</p>
            </template>
            <l-table class="table-hover table-striped"
                     :columns="table1.columns"
                     :data="table1.data">
            </l-table>
          </card>

        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Card from 'src/components/Cards/Card.vue'
import LTable from 'src/components/Table.vue'
const tableColumns = ['Id', 'Name', 'Salary', 'Country', 'City']
const tableData = [{
  id: 1,
  name: 'Dakota Rice',
  salary: '$36.738',
  country: 'Niger',
  city: 'Oud-Turnhout'
},
{
  id: 2,
  name: 'Minerva Hooper',
  salary: '$23,789',
  country: 'Curaçao',
  city: 'Sinaai-Waas'
},
{
  id: 3,
  name: 'Sage Rodriguez',
  salary: '$56,142',
  country: 'Netherlands',
  city: 'Baileux'
},
{
  id: 4,
  name: 'Philip Chaney',
  salary: '$38,735',
  country: 'Korea, South',
  city: 'Overland Park'
},
{
  id: 5,
  name: 'Doris Greene',
  salary: '$63,542',
  country: 'Malawi',
  city: 'Feldkirchen in Kärnten'
}]

export default {
  name: "DailyAnalysis",
  components: {
      LTable,
      Card
   },
  data: function () {
    return {
      series: [{
        name: 'PRODUCT A',
        data: [44, 55, 41, 67, 22, 43]
      }, {
        name: 'PRODUCT B',
        data: [13, 23, 20, 8, 13, 27]
      }, {
        name: 'PRODUCT C',
        data: [11, 17, 15, 15, 21, 14]
      }, {
        name: 'PRODUCT D',
        data: [21, 7, 25, 13, 22, 8]
      }],
      series2: [44, 55, 41, 17, 15],
      series3: [{
          name: "Desktops",
          data: [10, 41, 35, 51, 49, 62, 69, 91, 148]
      }],
      series4: [{
        name: 'PRODUCT A',
        data: [44, 55, 41, 67, 22, 43]
      }, {
        name: 'PRODUCT B',
        data: [13, 23, 20, 8, 13, 27]
      }, {
        name: 'PRODUCT C',
        data: [11, 17, 15, 15, 21, 14]
      }, {
        name: 'PRODUCT D',
        data: [21, 7, 25, 13, 22, 8]
      }],
      chartOptions: {
        chart: {
          type: 'bar',
          height: 350,
          stacked: true,
          toolbar: {
            show: true
          },
          zoom: {
            enabled: true
          }
        },
        responsive: [{
          breakpoint: 480,
          options: {
            legend: {
              position: 'bottom',
              offsetX: -10,
              offsetY: 0
            }
          }
        }],
        plotOptions: {
          bar: {
            horizontal: false,
            borderRadius: 10,
            borderRadiusApplication: 'end', // 'around', 'end'
            borderRadiusWhenStacked: 'last', // 'all', 'last'
            dataLabels: {
              total: {
                enabled: true,
                style: {
                  fontSize: '13px',
                  fontWeight: 900
                }
              }
            }
          },
        },
        xaxis: {
          type: 'datetime',
          categories: ['01/01/2011 GMT', '01/02/2011 GMT', '01/03/2011 GMT', '01/04/2011 GMT',
            '01/05/2011 GMT', '01/06/2011 GMT'
          ],
        },
        legend: {
          position: 'right',
          offsetY: 40
        },
        fill: {
          opacity: 1
        }
      },
      chartOptions2: {
        chart: {
          type: 'donut',
        },
        responsive: [{
          breakpoint: 480,
          options: {
            chart: {
              width: 200
            },
            legend: {
              position: 'bottom'
            }
          }
        }]
      },
      chartOptions3: {
        chart: {
          height: 350,
          type: 'line',
          zoom: {
            enabled: false
          }
        },
        dataLabels: {
          enabled: false
        },
        stroke: {
          curve: 'straight'
        },
        title: {
          text: 'Product Trends by Month',
          align: 'left'
        },
        grid: {
          row: {
            colors: ['#f3f3f3', 'transparent'], // takes an array which will be repeated on columns
            opacity: 0.5
          },
        },
        xaxis: {
          categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep'],
        }
      },
      chartOptions4: {
        chart: {
          type: 'bar',
          height: 350,
          stacked: true,
          toolbar: {
            show: true
          },
          zoom: {
            enabled: true
          }
        },
        responsive: [{
          breakpoint: 480,
          options: {
            legend: {
              position: 'bottom',
              offsetX: -10,
              offsetY: 0
            }
          }
        }],
        plotOptions: {
          bar: {
            horizontal: false,
            borderRadius: 10,
            borderRadiusApplication: 'end', // 'around', 'end'
            borderRadiusWhenStacked: 'last', // 'all', 'last'
            dataLabels: {
              total: {
                enabled: true,
                style: {
                  fontSize: '13px',
                  fontWeight: 900
                }
              }
            }
          },
        },
        xaxis: {
          type: 'datetime',
          categories: ['01/01/2011 GMT', '01/02/2011 GMT', '01/03/2011 GMT', '01/04/2011 GMT',
            '01/05/2011 GMT', '01/06/2011 GMT'
          ],
        },
        legend: {
          position: 'right',
          offsetY: 40
        },
        fill: {
          opacity: 1
        }
      },
      table1: {
        columns: [...tableColumns],
        data: [...tableData]
      },
    }
  },

  methods: {
    generateDayWiseTimeSeries: function (baseval, count, yrange) {
      var i = 0;
      var series = [];
      while (i < count) {
        var x = baseval;
        var y =
          Math.floor(Math.random() * (yrange.max - yrange.min + 1)) +
          yrange.min;
        
        series.push([x, y]);
        baseval += 86400000;
        i++;
      }
      return series;
    },
  },
};
</script>
<style>

</style>
