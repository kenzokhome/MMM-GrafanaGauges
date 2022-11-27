# MMM-GrafanaGauges
This [MagicMirror²] module allows you to display several gauges in a row generated by grafana.

<b>Important Note:</b> This module requires a running grafana installation. To install Grafana, follow the official [installation instructions](http://docs.grafana.org/installation/).

<b>[This blogpost](http://www.robstechlog.com/2017/06/30/personal-weather-chart-module/) describes how to install and use grafana and build a weatherchart.</b><br>
![example of a grafana weather gauges](https://github.com/SvenSommer/MMM-GrafanaGauges/blob/master/MMM-GrafanaGauges.png?raw=true)

## Installation of the module

In your terminal, go to your MagicMirror's Module folder:
````
cd ~/MagicMirror/modules
````

Clone this repository:
````
git clone https://github.com/SvenSommer/MMM-GrafanaGauges
````

Configure the module in your `config.js` file.

## Configuration

To use this module, you have to specify where your grafana installation is hosted and which gauges you'd like to display.

Add the module to the modules array in the `config/config.js` file:
````javascript
modules: [
	{
	 module: 'MMM-GrafanaGauges',
		 position: 'top_right',   // This can be any of the regions.
         header: 'Olive tree',
		 config: {
					host: "grafana_host", //Mandatory. See url when displaying within grafana
					port: 3000, // Mandatory.
					https: false, // Optional. Consider using TLS for your data. Default: false
					dashboardname: "flowers", // Mandatory.
					dashboardDB:"d-solo/asda",
					orgId: 1, // Mandatory.
					showIDs: [12, 8, 9, 10],// Mandatory. PanelId from the url.
					width: "100%", // Optional. Default: 100%
					height: "100%", // Optional. Default: 100%
					refreshInterval: 900 //Optional. Default: 900 = 1/4 hour
				}
	},
]
````

Everything needed is extractable from the <code>url</code> when you're viewing your gauge using grafana in your browser.<br>
<b>The <code>panelid</code> from each gauges has to be represented within the showIDs-array. Also the order set within this array.</b>

![url provides needed information](https://github.com/SvenSommer/MMM-GrafanaGauges/blob/master/url_explainend.png?raw=true)
## Optional configuration options

The following properties can be configured:


<table width="100%">
	<!-- why, markdown... -->
	<thead>
		<tr>
			<th>Option</th>
			<th width="100%">Description</th>
		</tr>
	<thead>
	<tbody>
		<tr>
			<td><code>width</code></td>
			<td>Width of the displayed chart. <code>'150 px'</code> or <code>'50 %'</code> are valid options.	<br><b>Default value:<code>"100%"</code></b></td>
		</tr>
		<tr>
			<td><code>height</code></td>
			<td>Height of the displayed chart. <code>'150 px'</code> or <code>'50 %'</code> are valid options.	<br><b>Default value:<code>"100%"</code></b></td>
		</tr>
			<tr>
			<td><code>refreshInterval</code></td>
			<td>Update interval of the diagram in seconds.
				<br><b>Default value:</b> <code>900</code>  = 15 \* 60 (four times every hour)
			</td>
		</tr>
	</tbody>
</table>
