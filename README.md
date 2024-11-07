# Major project Isye0269

This is the repository for IDEA9103 major project

Dynamic Particle Animation: A Time-Based Implementation of "The Scream"
Overview
An interactive animation system that transforms Edvard Munch's "The Scream" using time-based particle systems and dynamic color transitions. The implementation creates a mirrored display with independently animated particle systems for different regions of the artwork.
Interaction Instructions
Load the webpage in a modern browser supporting WebGL
The animation begins automatically, splitting into mirrored halves
Observe as particles flow across both sides with dynamic color transitions
Each region (sky, water, green areas, boardwalk) features unique particle behaviors
The animation runs continuously with particles regenerating periodically
Technical Implementation
Core Animation System
The animation utilizes a time-based approach with the following key components:
javascript
function animateCircles(circles, shape, shapeColour) {
    let pulse = sin(frameCount * 0.05) * 5;
    for (let i = 0; i < circles.length; i++) {
        let circle = circles[i];
        if (frameCounter >= circle.delay) {
            circle.x += circle.xSpeed;
            circle.y += circle.ySpeed;
            // Color and opacity updates
        }
    }
}

Particle Management System
Each region implements unique particle behaviors:
Sky Region: 2000 particles with 0.3 x-velocity
Water Region: 2000 particles with combined x/y velocities
Green Areas: 2000 particles with slower movement
Boardwalk: 7000 particles with negative velocities
Animation Properties
Time-Based Features
Frame counter-driven animations
Dynamic size pulsing using sine waves
Delayed particle spawning system
Synchronized color transitions
Color Management
Real-time color interpolation
Region-specific color mapping
Dynamic opacity control
Smooth color transitions every 120 frames
Technical Specifications
Core Components
Component	Parameters	Purpose
Particle System	Count: 2000-7000	Visual Elements
Frame Rate	30 FPS	Performance Optimization
Color Interpolation	0.05 step	Smooth Transitions
Size Pulsing	5px amplitude	Dynamic Movement
Performance Optimizations
Cached color lookups
Efficient particle recycling
Optimized draw calls
Buffer-based position management
Implementation Details
Particle Initialization
javascript
function initializeCircles(circles, shape, colour, count, xSpeed, ySpeed, size) {
    for (let i = 0; i < count; i++) {
        let { x: xPos, y: yPos } = findRandomColourPosition(shape, colour, false);
        circles.push({
            x: xPos,
            y: yPos,
            size: size + random(5),
            opacity: 0,
            fadeIn: true,
            delay: int(random(30, 150)),
            opacityDecayRate: random(1, 3)
        });
    }
}

External Tools and References
Core Technologies
p5.js for canvas manipulation
WebGL for rendering optimization
Custom time-based animation system
Inspiration Sources
Modern particle system implementations
Time-based animation techniques
Color interpolation methods from creative coding communities
Future Enhancements
Audio reactivity integration
Enhanced particle physics
Interactive user controls
Performance optimizations for mobile devices