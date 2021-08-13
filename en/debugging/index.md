# Monitoring and debugging

## Tracing
![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_2t4s71kc&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_0o42rvpp)

## Types of problems
![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_54dfwez2&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_qcmb1jeu)

## Debugging logical errors
![embed](https://api.eu.kaltura.com/p/120/sp/12000/embedIframeJs/uiconf_id/23449960/partner_id/120?iframeembed=true&playerId=kaltura_player&entry_id=0_2s1gcaht&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en_US&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[hotspots.plugin]=1&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=0_0c9irdya)


A simulation is used to obtain an image/idea of real scenarios, such that the outcomes of the simulations can be used in the 'real world'. It's effectively a *model*.

It is often hard to know whether a simulation is performed correctly simply by looking at the outcome. Often, you can analytically calculate the outcome, but this quickly becomes cumbersome. In addition, for many applications analytical solutions do not exist.

That's why it is so important to systematically check a simulation. Here are a few pointers that should aid in doing so:

1. Check using a pen and paper whether the core of your calculation is correct: are you working towards the right direction? If it becomes too complicated, it's sometimes better to make a rough estimation and compare that to your simulation.

2. Have you looked up the correct constants and formulas? Verify them another time. Are the constants precise enough? A rounding error can increase incredibly quickly!

3. For simulations based on time; are your time steps sufficiently small? If the outcome becomes very different by adapting the time step size, your time step is probably not small enough yet!

4. Are the components of the simulation in the correct order? Make sure each step calculates all values in the correct order. Only when that is done, check the values themselves and if those are correct.

Finally, a tip for debugging a simulation: you can print all values at each time step! This way, you can precisely inspect them and see if an error occurred at some point, or if maybe the starting values were already incorrect! Use Python's f-strings to clearly indicate  _what variable_ has _what value_ at _what moment_ in the simulation:

    while step < 1000:
        step += 1
        some_variable = step * 3

        print(f'some_variable has value {some_variable} at step number {step}')
