// setup
const canvas = document.querySelector('canvas')

const ctx = canvas.getContext('2d')
// define the fill color here for performance purpeses
context.fillStyle = 'ligthblue';

canvas.width = window.innerWidth
canvas.height = window.innerHeight


// classes 
class Particle{
    constructor(effect){
        this.effect = effect;
        this.x = Math.random() * this.effect.width;
        this.y = Math.random() * this.effect.height;
        this.radius = 15;
    }
    draw(context){
        context.beginPath();
        context.arc(this.x,this.y,this.radius,0,Math.PI * 2);
        context.fill()
    }
}

class Effect{
    constructor(canvas){
        this.canvas = canvas;
        this.width = this.canvas.width;
        this.height = this.canvas.height;
        this.particles = [];
        this.numberOfParticles = 20;
        this.createParticles()
    }
    createParticles(){
        for (let i = 0; i < this.numberOfParticles; i++) {
            this.particles.push(new Particle(this))
            
        }
    }
    handleParicles(context){
        this.particles.forEach(particle =>{
            particle.draw(context)
        })
    }

}
const effect = new Effect(canvas)
effect.handleParicles(ctx)

// animation
function animate() {
    requestAnimationFrame(animate)
}

animate()