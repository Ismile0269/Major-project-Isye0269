# Major project Isye0269

This is the repository for IDEA9103 major project

# Interactive Animation: The Scream - Time-Based Implementation

## How to Interact
1. Open the webpage in a modern browser supporting WebGL
2. The animation starts automatically, creating a mirrored display
3. Observe as particles flow dynamically across both halves
4. Each region (sky, water, green areas, boardwalk) features unique particle behaviors
5. The animation continues indefinitely with particles regenerating periodically

## Individual Animation Approach
I chose to implement a **time-based animation system** that transforms Edvard Munch's "The Scream" using dynamic particle systems. The animation employs frame counting and synchronized timing to create fluid motion across different regions of the artwork.

## Animation Driver Choice
**Time-Based Animation** was selected as the primary driver, implementing:
- Frame counter-driven animations (frameCounter variable)
- Delayed particle spawning system (30-150 frame delays)
- Synchronized pulse effects using sine waves
- Timed color transitions (every 120 frames)

## Unique Animation Properties
My implementation features several distinctive elements:

### Particle Systems
| Region | Particle Count | Velocity | Size |
|--------|---------------|----------|------|
| Sky | 2000 | x: 0.3, y: 0 | 16px |
| Water | 2000 | x: 0.3, y: -0.15 | 14px |
| Green Areas | 2000 | x: 0.15, y: -0.25 | 12px |
| Boardwalk | 7000 | x: -0.3, y: -0.4 | 10px |

### Dynamic Features
- Pulsing particle sizes using sine wave calculations
- Color interpolation with smooth transitions
- Independent opacity control for fade effects
- Time-based position updates

## Technical Implementation

### Core Animation System
```javascript
function animateCircles(circles, shape, shapeColour) {
    let pulse = sin(frameCount * 0.05) * 5;
    for (let i = 0; i < circles.length; i++) {
        let circle = circles[i];
        if (frameCounter >= circle.delay) {
            circle.x += circle.xSpeed;
            circle.y += circle.ySpeed;
            if (frameCounter % 120 === 0) {
                let newColor = color(random(255), random(255), random(255));
                circle.targetColour = newColor;
            }
        }
    }
}
```

### Particle Management
```javascript
function initializeCircles(circles, shape, colour, count, xSpeed, ySpeed, size) {
    for (let i = 0; i < count; i++) {
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
```

## Changes to Group Code
Enhanced the original implementation with:
- Addition of pulse effect using sine waves
- Implementation of color interpolation system
- Modified particle initialization parameters
- Improved time-based movement calculations

## External Tools and Techniques

### Core Technologies Used
- **p5.js**: Canvas manipulation and rendering
- **WebGL**: Performance optimization
- **Custom Animation System**: Time-based implementation

### Color Management
- Real-time color interpolation
- Region-specific color mapping
- Dynamic opacity control
- Frame-based color transitions

## Performance Optimizations
- Cached color lookups for efficiency
- Optimized particle recycling system
- Buffer-based position management
- Frame rate optimization (30 FPS)

## References and Inspiration

My approach was directed and constrained by an abiding respect for the iconic state of Edvard Munch's "The Scream" of 1893. Having designed the implementation of the central figure in our group project, I preferred the refining of its background via particle animation but without touching the core character of the painting. This conscious effort retains the iconic effect of the piece while presenting a layer of dynamism in interaction that complements rather than overshadows the original composition. This particle system is designed with an atmospheric effect in mind, echoing the emotional intensity of the painting without compromising its historical significance.

