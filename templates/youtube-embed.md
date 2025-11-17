---
updated_at: 2025-11-17T19:30:39.514+05:30
edited_seconds: 10
---
`<%* 
const url = await tp.system.prompt("Paste YouTube Link");
const videoID = url.split("v=")[1]?.split("&")[0] 
             || url.split("youtu.be/")[1]?.split("?")[0];

tR += `
<iframe width="560" height="315"
src="https://www.youtube.com/embed/${videoID}"
frameborder="0"
allowfullscreen></iframe>
`;
%>`
