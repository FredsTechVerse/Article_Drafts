### USING TANSTACK TABLE

- Previously known as react table extended to tanstack table to support other metaframeworks.
- Can work with JSON data as well as good old objects.
- As a headless UI ,it only gives us the functionality. It does not provide markup or styling which gives lots of flexibility to the dev to style it to preference via tailwindcss or use libraries like shadcn/ui.
- Component libraries provide ready markup for different components but come at the tradeoff of loosing flexibility "Bootstrap apps look like bootstrap app". However, they are a huge timesaver when it comes to implementing complex components like calendars , dropdowns and tooltips.
- To the useReactTable mother hook, we simply pass in our columns (documentation recommended to be in a separate file which we imported into the main tables component ) , data (Which was also being fetched from a separate file and imported into the tables component # NEXTJS FS is weird at first glance!) and any other hooks that we might need to achieve functionalities eg core row display hook (getCoreRowModel), pagination(getPaginationRowModel).

QUESTIONS
- How do i diplay columns conditionally ....
- How do i adjust the width of a column
- How do i access other properties about the specific row.
- How do i add a no to my columns... Simple.... Si lazima nitumie the registered data...
- How do i combine names ?
- How do i get to add additional functionalities?
- Ensure you register the hook for the respective functionalities to work as expected .
