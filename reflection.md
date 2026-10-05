# Reflection

I had AI help me create this website, RoseFrame. It's single browser and as the project asked, visualizes stack frame during a string copy into a smaller character buffer. 

I started by establishing the core architectural constraints with AI:
(The teaching part: Standardized input fields, presets, and safety toggles to demonstrate spatial memory behavior without weaponization

Browser execution: Self-contained single-file (`index.html`) running HTML, CSS, and vanilla JavaScript without any external backend dependence

Visual identity: Pretty and able to make abstract call stack concepts visually accessible


AI created the initial HTML layout, state machine, and CSS and my part was testing. Technical auditing and domain validation like making sure memory writes move toward higher memory addresses, tracking implicit null-terminators, and enforcing little-endian address representations)

this clarified cases in memory layout and mitigations:
Spatial Proximity: Visualizing the stack contiguous layout highlights why unmanaged writes are hazardous
off-by-one boundary:The `"Rosebud!"` preset (w 8 characters) shows off-by-one errors. While 8 printable characters match an 8-byte buffer, the required null terminator byte overflows into the adjacent stack
Defensive Controls: Implementing interactive toggles for bounds-checking  and stack canaries showed how modern compilers protect control flow before a corrupted return address is executed

By auditing the AI-generated code against class models, testing edge cases across presets, and iteratively refining the step animation, we created tool for demonstrating stack vulnerabilities
