
#INSTALLING ASTRO
- Use yarn to install and initialize astro `yarn astro add tailwind`. NPM is a bit rough around the edges.

# INITIALIZING TAILWINDCSS
- Installed via `yarn astro add tailwind`. Usually plug and play!

# EXCITING ASTRO FEATURES
- Simplicity - Uses the good old html , css  and javscript to build components. (No function based components)
- Flexibility - Integrates easily with UI framework of choice.
- Perfomance - Astro shines when dealing with content fetch and display.For mutations , nextjs is the best man for the job.
- Hosting - The hosting experience has been made seamless via netlify and vercel.
- Typescript support - Astro supports typescript out of the box.
- Reading props - Best illustrated with an example 
```astro 
---
interface Props {
	title: string;
	body: string;
	href: string;
}

const { href, title, body } = Astro.props;
---
```

- We use the `<slot/>` element to represent layout children. You know the elements that will be in between the layout tags.
- Data fetch has been made easier eliminationg async and usign await with the fetch api alone. Helps in content serving.
