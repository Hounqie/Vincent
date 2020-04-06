# Vincent
Nobody is Perfect >.&lt;
var textColor = function (bgColor) {
  var output = runNetwork(bgColor);
  if (output.black > .5) {
    return 'black';
  }
  return 'white';
}

var runNetwork = function anonymous(input) {
  var net = {"layers":[{"r":{},"g":{},"b":{}},{"0":{"bias":0.08934085891090618,"weights":{"r":-1.5012603706801122,"g":0.23790590715955792,"b":-0.7881913621665672}},"1":{"bias":1.6292172210368796,"weights":{"r":-2.9509956296225246,"g":1.3720055072870452,"b":-1.4362576143848105}},"2":{"bias":2.1208013072468117,"weights":{"r":-3.6304389974602604,"g":1.779168215022672,"b":-1.5176988004592173}}},{"black":{"bias":-3.15973680772982,"weights":{"0":1.2912961025983756,"1":3.8380004817552225,"2":4.848147283911926}}}],"outputLookup":true,"inputLookup":true};

  for (var i = 1; i < net.layers.length; i++) {
    var layer = net.layers[i];
    var output = {};
    
    for (var id in layer) {
      var node = layer[id];
      var sum = node.bias;
      
      for (var iid in node.weights) {
        sum += node.weights[iid] * input[iid];
      }
      output[id] = (1 / (1 + Math.exp(-sum)));
    }
    input = output;
  }
  return output;
}
