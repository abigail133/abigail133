<h1 align="center">Hi👋, I'm Abigail </h1>
 
- Check out my portfolio. I have experience in website management and web development. [here](https://energysolutions.egat.co.th/)!

Actually working on:
 
- In the past, on the job learning May not be in the line of work that I want
- so I can learn that The working system of each line of work may not be the same
- but in our work But ready to start learning in the line that you want to do
- such as programming who have never worked in this line before
- Reason for leaving the job because I want to work in line with myself

 -----------------
 
Experiences I've had 🤏

- Frontend Development: HTML, CSS , Bootstrap, JavaScript 
- Frameworks: Joomla 4, Node.js
- Programming Languages: Java, Python , PHP
- Databases: SQL 
- Tools: Power BI, Software Tester
- Analytics
- API

-----------------

Actually working on:
- Materiale per Ingegneria Informatica, italian Repo for Computer Engineering at UNIPI
- destreamer-unipi, porting of Destreamer for UNIPI (Download videos from Microsoft Stream)

### Skills


<p align="left">
<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/javascript-colored.svg" width="36" height="36" alt="JavaScript" /></a>
<a href="https://www.python.org/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/python-colored.svg" width="36" height="36" alt="Python" /></a>
<a href="https://www.php.net/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/php-colored.svg" width="36" height="36" alt="PHP" /></a>
<a href="https://docs.microsoft.com/en-us/dotnet/csharp/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/csharp-colored.svg" width="36" height="36" alt="C#" /></a>
<a href="https://developer.mozilla.org/en-US/docs/Glossary/HTML5" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/html5-colored.svg" width="36" height="36" alt="HTML5" /></a>
<a href="https://www.w3.org/TR/CSS/#css" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/css3-colored.svg" width="36" height="36" alt="CSS3" /></a>
<a href="https://nodejs.org/en/" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/nodejs-colored.svg" width="36" height="36" alt="NodeJS" /></a>
</p>

import React, { useContext } from "react";
import { StateContext } from "../pages/_app";
import FormLabel from "./forms/FormLabel";
import ExtraSmallTick from "./misc/ExtraSmallTick";
import { useTheme } from "next-themes";
import { iconData } from "../pages/_app";

const IconSelector = ({ handleIconToggle, title, iconType }) => {
  const { state } = useContext(StateContext);
  const { theme } = useTheme();

  return (
    <article className="flex flex-col flex-1 w-full dark:bg-dark-700 bg-light-100 p-3 rounded-md transition-all duration-150 ease-in-out">
      <div className="mb-2">
        <FormLabel text={title} icon={"💻"} />
      </div>
      <div className="flex flex-wrap text-4xl gap-x-2 gap-y-2">
        {iconData[iconType].map((icon, index) => {
          return (
            <button
              key={`${icon.path}`}
              className="relative flex w-auto overflow-visible group"
              alt={`${icon.name}`}
              onClick={() => {
                handleIconToggle(iconType, icon, index);
              }}
            >
              <div className="absolute z-40 hidden px-2 py-2 rounded-md w-28 group-hover:flex dark:bg-dark-600 bg-light-200 -bottom-12 transform -left-7">
                <p className="mx-auto mb-0 text-xs font-semibold tracking-wide text-light-600 dark:text-white">
                  {icon.name}
                </p>
              </div>
              {state.skills[iconType].some(
                (item) => item.name === icon.name
              ) ? (
                <div className="absolute top-0 left-0 w-4 h-4 p-0 overflow-hidden text-xs bg-white border-0 rounded-lg z-10">
                  <ExtraSmallTick />
                </div>
              ) : null}

              <i
                className={`${icon.iTag} w-9 h-9 ${
                  state.skills[iconType].some((item) => item.name === icon.name)
                    ? "colored"
                    : "text-light-400 dark:text-light-500"
                }`}
              ></i>
            </button>
          );
        })}
      </div>
    </article>
  );
};

export default IconSelector;
