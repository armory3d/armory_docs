# Machine Learning

## Intro

Tensorflow library for Kha is available for machine learning experiments.

- Example at [GitHub](https://github.com/armory3d/tensorflow_example)

```haxe
package arm;

import tf.TF;
import tf.TFHelper;

class MyTrait extends iron.Trait {
	public function new() {
		super();

		notifyOnInit(function() {
			TFHelper.init(function() {
				var model = TF.sequential();
				model.add(TF.layers.dense({units: 1, inputShape: [1]}));
				model.compile({loss: 'meanSquaredError', optimizer: 'sgd'});
				var xs = TF.tensor2d([1, 2, 3, 4], [4, 1]);
				var ys = TF.tensor2d([1, 3, 5, 7], [4, 1]);
				model.fit(xs, ys).then(function() {
					var res = model.predict(TF.tensor2d([5], [1, 1]));
					trace(res);
				});
			});
		});
	}
}
```
