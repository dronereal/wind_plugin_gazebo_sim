# wind_plugin_gazebo_sim
Instructions for connecting the wind plugin to gazebo sdf world

## Example of usage wind plugin in gazebo world:
https://github.com/gazebosim/gz-sim/blob/af73ebe7c8c693fd54e391f79c11bf9f24df2640/examples/worlds/wind.sdf
## To include wind plugin in your world you need to copy this in world file:
<!-- Load the plugin for the wind -->
    <plugin
      filename="gz-sim-wind-effects-system"
      name="gz::sim::systems::WindEffects">
      <force_approximation_scaling_factor>1</force_approximation_scaling_factor>
      <horizontal>
        <magnitude>
          <time_for_rise>10</time_for_rise>
          <sin>
            <amplitude_percent>0.05</amplitude_percent>
            <period>60</period>
          </sin>
          <noise type="gaussian">
           <mean>0</mean>
           <stddev>0.0002</stddev>
          </noise>
        </magnitude>
        <direction>
          <time_for_rise>30</time_for_rise>
          <sin>
            <amplitude>5</amplitude>
            <period>20</period>
          </sin>
          <noise type="gaussian">
           <mean>0</mean>
           <stddev>0.03</stddev>
          </noise>
        </direction>
      </horizontal>
      <vertical>
        <noise type="gaussian">
         <mean>0</mean>
         <stddev>0.03</stddev>
        </noise>
      </vertical>
    </plugin>

### It's include plugin in your world 

## After copy include this lines:
    <wind>
      <linear_velocity>1 0 1</linear_velocity>
    </wind>

### it make initial velocity along the axes setup 

## Finally you can add: 

    <enable_wind>true</enable_wind>

you should add this to the model, which should be influenced by the wind

I simulate zephyr airplane model. It's my example:
 
    <include>
      <uri>model://zephyr_with_ardupilot</uri>
      <pose degrees="true">0 0 0.422 -90 0 180</pose>
      <enable_wind>true</enable_wind>
    </include>
