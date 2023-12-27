# Implementation of A* and Dijkstra on an occupancy grid map

The A* and Dijkstra algorithm employed are developed using the `heapq` data type in python. The given A* and Dikstra are guaranteed to be efficient and fast.

## Binary Grid Map generation:

```
class PerceptionMapper:
    def __init__(self, image, resolution):
        self.map = self.initialiseMap(image)
        # height, width
        self.size = self.map.shape
        self.defaultResolution = resolution

    def initialiseMap(self, testImage):
        env = np.ones(testImage.shape)  
        for i in range(testImage.shape[0]):
            for j in range(testImage.shape[1]):
                if testImage[i][j] < 125: 
                    env[i][j] = 0

        return env
```

A* and Dijkstra algorithms takes the map from the above lines of code which creat map object. Ony requirement here is to have a numpy array of occupancy grid. Once you obtain an occupancy grid map, the occupancy grid map consists of the free space and obstacles data. This could be extracted for our use by providing it some binary values, i.e., 1 for free space and 0 for obstacles based on the pixel intensity. Usually, when an obstacle is present, the intensity would be lower in comparison to free space region. You could use a suitable threshold value, in my case I'm using a threshold of 125. Once you have a binary grid map, you could construct a graph and go ahead with the planning algorithms.

#### For other code explanations, please take a look at the comments added along with the raw code.
