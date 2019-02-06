------->>>>>>>HTML

<!DOCTYPE html>
<html>
<head>
	<title>var - 0</title>
	<link rel="stylesheet" type="text/css" href="main.css">
</head>
<body>
	<div class="main">
		<div class="sidebar">
			<div class="sidebar-item">1</div>
			<div class="sidebar-item">2</div>
			<div class="sidebar-item">3</div>
			<div class="sidebar-item">4</div>
		</div>
		<div class="view">
			<div class="top">top</div>
			<div class="bottom">bottom</div>			
		</div>
	</div>
</body>
</html>


------->>>>>>>CSS

*{
	box-sizing: border-box;
	border : 1px solid black;
	margin : 0px;
	padding: 0px;
	font-size: xx-large;
}

.main{
	display : grid;
	width: 80vw;
	height: 80vh;
	text-align: center;
	line-height: 100%;
	grid-template-columns: 20vw 60vw;
	grid-template-rows: 80vh;
	grid-template-areas: 
		"sidebar view"
		;
}

.sidebar{
	grid-area : sidebar;
}

.sidebar-item{
	height : 20vh;
}	

.view{
	grid-area : view;
}

.top{
	height : 20vh;
}

.bottom{
	height : 60vh;
}



------->JS

function distance(first, second){

	if(!Array.isArray(first) || !Array.isArray(second)){
		throw new Error("Conversion error");
	}
	
	let arr1 = [...new Set(first)];
	let arr2 = [...new Set(second)];
	
	let dist = 0;
	
	arr1.map((element, index) => {
		
		if(arr2.includes(element)){
			arr2.splice(index, 1);
		} else {
			dist++;
		}
	})
	
	dist += arr2.length;
	
	return dist;
}



function distance(first, second){
	if (!Array.isArray(first) || !Array.isArray(second)){
		throw new Error('InvalidType')
	}
	let me = [...new Set(first)]
	let other = [...new Set(second)]
	let diffCount = 0
	for (let item of me){
		if (other.indexOf(item) === -1){
			diffCount++
		}
		else{
			other.splice(other.indexOf(item), 1)			
		}
	}
	diffCount += other.length
	return diffCount
}




------->>>JSON

{
	"invoiceNumber": 1,
	"invoiceSeries": "ABCD",
	"invoiceItems": [{
		"productName": "Product 1",
		"quantity": 10,
		"productPrice": 10.00
	}, {
		"productName": "Product 2",
		"quantity": 10,
		"productPrice": 100.00
	}]
}




<!DOCTYPE html>
<html>


<head>

</head>

<body>
    <script>
        var ourRequest = new XMLHttpRequest();
        ourRequest.onreadystatechange = () => {
            var ourData = JSON.stringify(ourRequest.responseText);
            ourData = JSON.parse(ourData);
            var div = document.createElement('div');
            div.innerHTML = ourData;
            div.id = 'json';
            document.getElementsByTagName('body')[0].appendChild(div);
        }
        ourRequest.open('GET', 'invoice.json', true);
        ourRequest.send();
    </script>
</body>

</html>




-------->>>REST

app.post('/authors', async (req, res) => {
	
	if(!req.body.name || !req.body.email || !req.body.age){
		return res.status(500).send({message: "server error"});
	}
	
	let pattern = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
	if(!pattern.test(req.body.email)){
		res.status(500).json({message : 'email is not valid'})
	}
	
	try{
		let author = new Author(req.body)
		await author.save()
		res.status(201).json({message : 'created'})
	}
	catch(err){
		// console.warn(err.stack)
		res.status(500).json({message : 'server error'})		
	}
})



------------>>>>>REACT


// TODO : adăugați o componentă Robot 
// afișați o componentă Robot pentru fiecare robot din stare 
// o componentă robot ar trebui să afișeze un robot și să permită ștergerea lui

import React, { Component } from 'react'

class Robot extends Component {
  render() {
  	let {item} = this.props
    return (
      <div>
  		Hello, my name is {item.name}. I am a {item.type} and weigh {item.mass}
  		<input type="button" value="delete" onClick={() => this.props.onDelete(item.id)} />
      </div>
    )
  }
}

export default Robot
