
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The Cook Book</title>
<style>
:root{ color-scheme: light; }
*{ box-sizing:border-box; }
html,body{ margin:0; padding:0; }
body{
  background:#faf7f2; color:#2b2622;
  font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif;
  line-height:1.5;
}
.wrap{ max-width:920px; margin:0 auto; padding:28px 20px 80px; }
header.masthead{ text-align:center; padding:26px 16px 22px; border-bottom:2px solid #e7ddcc; margin-bottom:22px; }
.masthead h1{ font-family:Georgia,"Times New Roman",serif; font-size:40px; letter-spacing:.5px; margin:0 0 6px; }
.masthead p{ margin:0; color:#8a7f6f; font-style:italic; }
.count-pill{ display:inline-block; margin-top:12px; background:#5a4a3a; color:#fff; font-size:13px; padding:4px 12px; border-radius:999px; }

.toolbar{ display:flex; gap:10px; flex-wrap:wrap; align-items:center; margin-bottom:20px; }
.toolbar input[type=search]{
  flex:1 1 240px; min-width:200px; padding:10px 14px; border:1px solid #d9cdb8; border-radius:10px;
  font-size:15px; background:#fff;
}
.toolbar select{ padding:10px 12px; border:1px solid #d9cdb8; border-radius:10px; background:#fff; font-size:14px; }
.btn{
  border:0; border-radius:10px; padding:10px 16px; font-size:14px; font-weight:600; cursor:pointer;
}
.btn-primary{ background:#b5562a; color:#fff; }
.btn-primary:hover{ background:#9c4622; }
.btn-ghost{ background:#efe7d8; color:#5a4a3a; }
.btn-ghost:hover{ background:#e6dcc8; }

/* Index */
.index{ background:#fff; border:1px solid #ead; border-color:#ece2d0; border-radius:14px; padding:18px 22px; margin-bottom:26px; }
.index h2{ font-family:Georgia,serif; font-size:20px; margin:0 0 4px; }
.index .sub{ color:#8a7f6f; font-size:13px; margin:0 0 14px; }
.cat-block{ margin-bottom:12px; }
.cat-block .cat-name{ font-weight:700; font-size:13px; text-transform:uppercase; letter-spacing:.6px; color:#b5562a; margin-bottom:4px; }
.cat-block ol{ margin:0; padding:0; list-style:none; }
.cat-block li{ display:flex; justify-content:space-between; gap:10px; padding:3px 0; border-bottom:1px dotted #ece2d0; font-size:14px; cursor:pointer; }
.cat-block li:hover{ color:#b5562a; }
.cat-block li .num{ color:#a99c87; font-variant-numeric:tabular-nums; }
.cat-empty{ color:#bcae97; font-style:italic; font-size:13px; }

/* Recipe cards */
.recipe{
  background:#fff; border:1px solid #ece2d0; border-radius:14px; padding:22px 24px; margin-bottom:18px;
  scroll-margin-top:14px;
}
.recipe .rnum{ font-size:12px; font-weight:700; letter-spacing:1px; text-transform:uppercase; color:#b5562a; }
.recipe h3{ font-family:Georgia,serif; font-size:25px; margin:2px 0 6px; line-height:1.2; }
.recipe .meta{ color:#8a7f6f; font-size:13px; margin-bottom:4px; }
.recipe .cat-tag{ display:inline-block; background:#f2ecde; color:#7a6a55; font-size:11px; font-weight:600; text-transform:uppercase; letter-spacing:.5px; padding:3px 9px; border-radius:6px; margin-bottom:12px; }
.recipe .source{ color:#a99c87; font-size:12px; font-style:italic; margin-bottom:10px; }
.recipe .note{ font-size:14px; color:#4a4036; margin:0 0 14px; }
.cols{ display:grid; grid-template-columns:1fr 1.4fr; gap:24px; }
@media(max-width:620px){ .cols{ grid-template-columns:1fr; gap:14px; } .masthead h1{ font-size:32px; } }
.cols h4{ font-size:12px; text-transform:uppercase; letter-spacing:.7px; color:#5a4a3a; margin:0 0 8px; border-bottom:1px solid #ece2d0; padding-bottom:5px; }
.ing{ margin:0; padding:0; list-style:none; }
.ing li{ font-size:14px; padding:3px 0 3px 16px; position:relative; }
.ing li:before{ content:"•"; color:#b5562a; position:absolute; left:0; }
.ing li.subhead{ font-weight:700; color:#7a6a55; padding-left:0; margin-top:6px; }
.ing li.subhead:before{ content:""; }
.dir{ margin:0; padding:0 0 0 4px; list-style:none; counter-reset:step; }
.dir li{ font-size:14px; padding:5px 0 5px 30px; position:relative; }
.dir li:not(.subhead){ counter-increment:step; }
.dir li:not(.subhead):before{
  content:counter(step); position:absolute; left:0; top:5px; width:21px; height:21px;
  background:#b5562a; color:#fff; border-radius:50%; font-size:12px; font-weight:700;
  display:flex; align-items:center; justify-content:center;
}
.dir li.subhead{ font-weight:700; color:#7a6a55; padding-left:0; margin-top:8px; }

.empty-state{ text-align:center; color:#a99c87; padding:40px 0; font-style:italic; }
.badge-new{ display:inline-block; background:#3c7a4a; color:#fff; font-size:10px; font-weight:700; padding:2px 7px; border-radius:5px; margin-left:8px; vertical-align:middle; letter-spacing:.5px; }

/* Modal */
.modal-bg{ position:fixed; inset:0; background:rgba(40,32,24,.5); display:none; align-items:flex-start; justify-content:center; padding:30px 16px; overflow-y:auto; z-index:50; }
.modal-bg.open{ display:flex; }
.modal{ background:#fff; border-radius:16px; max-width:640px; width:100%; padding:24px 26px; box-shadow:0 20px 60px rgba(0,0,0,.25); }
.modal h2{ font-family:Georgia,serif; margin:0 0 4px; font-size:24px; }
.modal .hint{ color:#8a7f6f; font-size:13px; margin:0 0 18px; }
.field{ margin-bottom:14px; }
.field label{ display:block; font-size:13px; font-weight:600; color:#5a4a3a; margin-bottom:5px; }
.field input,.field select,.field textarea{ width:100%; padding:9px 12px; border:1px solid #d9cdb8; border-radius:9px; font-size:14px; font-family:inherit; background:#fff; }
.field textarea{ resize:vertical; min-height:90px; }
.field .tip{ font-size:12px; color:#a99c87; margin-top:4px; }
.modal-actions{ display:flex; justify-content:flex-end; gap:10px; margin-top:6px; }
.row2{ display:grid; grid-template-columns:1fr 1fr; gap:12px; }
@media(max-width:520px){ .row2{ grid-template-columns:1fr; } }
.footer-note{ text-align:center; color:#bcae97; font-size:12px; margin-top:30px; }
</style>
</head>
<body>
<div class="wrap">
  <header class="masthead">
    <h1>The Cook Book</h1>
    <p>A collection of recipes worth keeping</p>
    <div class="count-pill" id="countPill">0 recipes</div>
  </header>

  <div class="toolbar">
    <input type="search" id="search" placeholder="Search recipes or ingredients…" autocomplete="off">
    <select id="catFilter"><option value="">All categories</option></select>
    <button class="btn btn-primary" id="addBtn">+ Add recipe</button>
    <button class="btn btn-ghost" id="resetBtn" title="Restore the original recipes and clear ones you added">Reset</button>
  </div>

  <section class="index" id="indexBox">
    <h2>Index by Dish Type</h2>
    <p class="sub">Recipes are filed by type and numbered in the order they are added. New recipes are appended at the back and listed here for quick reference.</p>
    <div id="indexBody"></div>
  </section>

  <div id="recipeList"></div>
  <div class="footer-note">Your additions are saved on this device and reappear every time you open this page.</div>
</div>

<!-- Add Recipe Modal -->
<div class="modal-bg" id="modalBg">
  <div class="modal">
    <h2>Add a recipe</h2>
    <p class="hint">It’s filed under the category you pick, auto-numbered, and saved so it shows up every time you open the cookbook.</p>
    <div class="field">
      <label>Recipe name</label>
      <input id="f_title" placeholder="e.g. Grandma’s Apple Pie">
    </div>
    <div class="row2">
      <div class="field">
        <label>Category</label>
        <select id="f_cat"></select>
      </div>
      <div class="field">
        <label>Meta line (optional)</label>
        <input id="f_meta" placeholder="Prep 15 min · Cook 30 min · Serves 4">
      </div>
    </div>
    <div class="field">
      <label>Source / note (optional)</label>
      <input id="f_source" placeholder="From Mom’s recipe card">
    </div>
    <div class="field">
      <label>Ingredients</label>
      <textarea id="f_ing" placeholder="One per line.&#10;Tip: a line ending with a colon (For the sauce:) becomes a sub-heading."></textarea>
    </div>
    <div class="field">
      <label>Directions</label>
      <textarea id="f_dir" placeholder="One step per line.&#10;Tip: a line ending with a colon becomes a sub-heading."></textarea>
    </div>
    <div class="modal-actions">
      <button class="btn btn-ghost" id="cancelBtn">Cancel</button>
      <button class="btn btn-primary" id="saveBtn">Save recipe</button>
    </div>
  </div>
</div>

<script>
const CATEGORIES = ["Appetizers & Starters","Soups & Salads","Chicken & Poultry","Beef & Pork","Seafood","Pasta & Noodles","Vegetarian & Sides","Breakfast & Brunch","Desserts & Sweets","Drinks"];
const STORAGE_KEY = "cookbook_user_recipes_v1";
const CG = "Adapted from Campo Grande (eatcampogrande.com)";

// ---- Seed data: all 20 recipes from the Pages cookbook ----
const SEED = [
{num:1,cat:"Chicken & Poultry",title:"Garlic Butter Chicken Bites with Creamy Parmesan Pasta",meta:"Prep 10 min · Cook 20 min · Total 30 min · Serves 4",
 ing:["1 lb chicken breast, cubed","8 oz pasta (penne or rotini)","4 tbsp butter","2 cloves garlic, minced","1 cup heavy cream","1 cup Parmesan cheese, grated","Salt and pepper to taste","Fresh basil for garnish"],
 dir:["Cook pasta according to package instructions; drain.","In a skillet, melt butter over medium heat. Add garlic and chicken, cooking until chicken is golden brown.","Stir in heavy cream and Parmesan cheese, cooking until creamy. Season with salt and pepper.","Toss cooked pasta in the sauce, serving garnished with fresh basil."]},
{num:2,cat:"Beef & Pork",title:"Iberico Pork Presa with Chimichurri & Red Pepper Puree",meta:"Serves 4",source:CG,
 ing:["Iberico pork presa","Pimentón (smoked paprika)","Ground cumin","Salt and black pepper","Fresh parsley","Fresh oregano","Garlic cloves","Green chili","Shallots","Spanish anchovy fillets","Sherry vinegar","Extra virgin olive oil","Red peppers and piquillo peppers","White wine and vinegar","Chickpeas (for frying)"],
 dir:["For the spiced salt:","Mix half of the pimentón and half of the cumin with a teaspoon of salt. Set aside.","For the chimichurri:","Mix the parsley, oregano, garlic cloves, green chili, shallots, Spanish anchovy fillets, sherry vinegar, extra virgin olive oil, and black pepper together in a bowl. Add the other half of the pimentón and cumin. Season with salt and pepper.","Cook for 10 minutes.","For the red pepper puree:","Soak the shallots and garlic cloves in olive oil for 5 minutes. Add the red and piquillo peppers. Add vinegar and white wine.","Meanwhile, heat a saucepan of oil to 356°F. Deep fry the chickpeas for 2 minutes. Drain and toss in the spiced salt.","Add both mixtures to a blender and blend for a few minutes, until completely smooth.","For the pork:","Sear both sides of the presa for 3 minutes each side. Add another minute or two if you don’t want the presa to be pink.","Slice the pork onto a serving plate. Spoon the chimichurri over the pork. Add two spoonfuls of the puree on the side. Coat the presa with the chickpeas."]},
{num:3,cat:"Beef & Pork",title:"Iberico Pork Fillet with Pedro Ximénez Sauce",meta:"Serves 4",source:CG,
 ing:["Iberico pork fillet","Garlic cloves","Fresh thyme","Butter","Shallots, chopped","Pedro Ximénez sherry","Chicken stock"],
 dir:["Preheat the oven to 400°F.","Prepare the pork, then sear both sides in a hot frying pan.","Add garlic cloves, thyme, and a tablespoon of butter over the pork fillet.","Place the pork into the oven and bake for 8 minutes, basting halfway through.","Make the Ximénez sauce: add butter to the pan you seared the pork in, and fry some chopped shallots and thyme. Add Pedro Ximénez sherry. Bring to a boil, add the chicken stock, and reduce the heat. It’s ready when it becomes syrupy."]},
{num:4,cat:"Beef & Pork",title:"Iberico Pork Loin with Sherry Roasted Tomatoes",meta:"Serves 4",source:CG,
 ing:["Iberico pork loin","Tomatoes","Peppers","Garlic","Sherry","Butter","Fennel seeds","Olive oil","Bread (for picada)","Picada oil and fried garlic"],
 dir:["Preheat the oven to 365°F.","Season the pork and set it aside to reach room temperature.","Put the tomatoes, peppers, garlic, sherry, and butter in a roasting tin sprinkled with fennel seeds. Drizzle some oil on top and roast for 30 minutes.","Brush the bread with picada oil and toast in a skillet.","Add the bread, fried garlic, and oil to a food processor and process until finely chopped. Mix in a bowl and set aside.","Sear the pork on both sides for 2–3 minutes.","Remove the veggies from the oven after 30 minutes. Add the pork, turn the oven down to 320°F, and roast for 10–15 minutes until the pork reaches the desired doneness.","Rest the pork for 5–10 minutes.","Divide the servings. Drizzle the cooking liquids over the serving plates, then drizzle the picada over the dish."]},
{num:5,cat:"Beef & Pork",title:"Iberico Pork Pesto on Toast",meta:"Serves 4",source:CG,
 ing:["Iberico dry-cured sausage","Almonds","Cheese","Lemon juice","Peppers","Garlic","Fresh parsley","Bread","Butter"],
 dir:["Add the dry sausage, almonds, cheese, lemon juice, peppers, garlic, and parsley to a food processor. Blitz until smooth.","Bring a pan or skillet to a high heat. Toast the bread with butter.","Top the toasted bread with the pork sausage pesto."]},
{num:6,cat:"Beef & Pork",title:"Presa Iberico with Mojo Verde",meta:"Serves 4",source:CG,
 ing:["Iberico pork presa","Garlic","Salt","Fresh cilantro","Fresh parsley","Cumin seeds","Olive oil","Sherry vinegar","Water"],
 dir:["Use a pestle and mortar to grind the garlic and salt into a paste. Add the cilantro, parsley, and cumin seeds and keep grinding. Slowly add olive oil, sherry vinegar, and water. Stir until combined.","Set the grill or skillet to a high heat. Sear the presa on both sides for 2–3 minutes.","Rest the meat for 5 minutes.","Add the mojo verde seasoning and serve."]},
{num:7,cat:"Beef & Pork",title:"Iberico Pork Fillet with Trintxat Potatoes",meta:"Serves 4",source:CG,
 ing:["Iberico pork fillet","Potatoes","Cabbage","Salt","Bacon","Garlic","Olive oil","Marinade or dry rub of choice"],
 dir:["Marinate or season the pork.","To make the trintxat, boil the potatoes and cabbage in salted water for 20 minutes. Drain and then mash together.","Fry the bacon and garlic in some olive oil. Add the mashed potatoes and cabbage and mix well.","Heat the oven to 435°F.","Retrieve the pork from the marinade or dry rub. Sear in a hot pan on both sides for 2–3 minutes.","Transfer the pork to the oven and cook for 20–25 minutes until heated through. The thickest part should reach at least 150°F.","Remove the pork from the oven and let it rest for 5 minutes before serving."]},
{num:8,cat:"Beef & Pork",title:"Roasted Iberico Pork Secreto with Potatoes",meta:"Serves 4",source:CG,
 ing:["Iberico pork secreto","Potatoes","White wine","Honey","Salt and pepper"],
 dir:["For the potatoes:","Clean the potatoes and cut them into slices. Lay them in a single layer on a baking sheet and season well.","Pour half of the white wine over the potatoes. Roast for 30 minutes at 350°F.","For the pork:","Season the pork to your liking and place it over the roasted potatoes.","Spread honey over the pork with a kitchen brush.","Roast everything again at 350°F for 30 minutes.","Let the pork rest 5 minutes before serving."]},
{num:9,cat:"Beef & Pork",title:"Iberico Pork Tenderloin with Charred Red Pepper Sauce",meta:"Serves 4",source:CG,
 ing:["Iberico pork tenderloin","Red bell peppers","Olive oil","Garlic","Onions","Salt and pepper"],
 dir:["Let the tenderloin reach room temperature.","For the sauce:","Roast the bell peppers over medium heat until charred on both sides, then set aside.","Heat some oil in a pan. Add the garlic and onions and cook for 7 minutes.","Peel, seed, and chop the red bell pepper and add it to the pan.","Blend until smooth in a food processor. Add olive oil, salt, and pepper.","For the pork:","Heat the oven to 400°F.","Sear the tenderloin on both sides in a hot pan for 2–3 minutes each side.","Transfer to a baking dish with the sauce and roast for 1–3 minutes.","Let it rest for 5–10 minutes before serving."]},
{num:10,cat:"Beef & Pork",title:"Iberico Pork with Oyster Mushrooms",meta:"Serves 4",source:CG,
 ing:["Iberico pork","Black pepper","Brown sugar","Whiskey (for marinade)","Oyster mushrooms","Onion","Pepper","Carrots","Tomato puree","Water"],
 dir:["Cut the meat into large chunks. Season with black pepper and brown sugar. Marinate in whiskey for 2–3 hours.","Clean and cut the mushrooms.","Puree the onion, pepper, and a carrot in a blender and cook in heated oil.","Slice the remaining carrot into coins.","Add the veggies (excluding the mushrooms) to the puree and sauté for 2–3 minutes.","Add the tomato puree and a cup of water, then cook with the pork, covered, for 35 minutes.","Add the mushrooms in the last 10 minutes.","Let it rest for 5 minutes before serving."]},
{num:11,cat:"Beef & Pork",title:"Iberico Pork Potato Casserole",meta:"Serves 4",source:CG,
 ing:["Iberico pork steaks","Ground cumin","Paprika","Fennel seeds","Olive oil","Tomato","Onion","Potatoes"],
 dir:["Mix the cumin, paprika, fennel seeds, and olive oil in a large bowl.","Place the pork in the bowl and set it aside to marinate.","Peel and slice the tomato and onion.","Warm the olive oil in a casserole pot. Soften the onions for 5 minutes before adding the potatoes and tomatoes.","Simmer the mixture, then place in the oven at 350°F for 15 minutes.","Drain the oil from the marinating pork into a frying pan. Heat the oil until smoking.","Add the pork and sear on both sides for 2–3 minutes.","Pour the juices and spices into the casserole dish and stir.","Add the pork steaks and place them on top. Cook uncovered for 10 minutes.","Let it rest for 5 minutes before serving."]},
{num:12,cat:"Drinks",title:"Woodford Reserve Old Fashioned",meta:"Prep 3 min · Total 3 min · Serves 1",source:"Adapted from Woodford Reserve (woodfordreserve.com)",
 ing:["2 oz Woodford Reserve Bourbon","1 sugar cube (or 1 tsp sugar)","A splash of water","2 dashes aromatic (Angostura) bitters","Cherry and orange (or lemon) peel, for garnish"],
 dir:["In an Old Fashioned glass, add the sugar and water. Stir to dissolve the sugar.","Add 2 dashes of aromatic bitters and 2 oz Woodford Reserve Bourbon.","Stir, then add ice.","Garnish with a cherry and an expressed orange or lemon peel."]},
{num:13,cat:"Beef & Pork",title:"Beef Wellington",meta:"Prep 45 min · Cook 45 min · Total 1 hr 30 min (plus chilling) · Serves 6",
 ing:["2–2½ lb center-cut beef tenderloin (filet)","Salt and black pepper","2 tbsp olive oil","2 tbsp Dijon mustard","1 lb cremini or button mushrooms, finely chopped","2 shallots, minced","2 cloves garlic, minced","2 tbsp butter","1 tsp fresh thyme leaves","8–10 slices prosciutto","1 sheet (about 14 oz) puff pastry, thawed","2 egg yolks, beaten (egg wash)","Flour, for dusting"],
 dir:["Season the tenderloin generously with salt and pepper. Heat olive oil in a skillet over high heat and sear the beef on all sides until browned, about 2–3 minutes per side. Let cool, then brush all over with Dijon mustard.","Make the duxelles: melt butter in the same skillet, add shallots, garlic, mushrooms, and thyme. Cook over medium heat, stirring, until all moisture evaporates and the mixture is dry, 10–15 minutes. Season and let cool.","Lay a large sheet of plastic wrap on the counter. Arrange the prosciutto in an overlapping layer, spread the duxelles evenly over it, then place the beef on top. Using the wrap, roll the prosciutto and mushrooms tightly around the beef. Twist the ends and chill 15–20 minutes.","Roll out the puff pastry on a floured surface. Unwrap the beef, set it on the pastry, and wrap snugly, trimming excess and sealing the seam. Brush with egg wash and chill 15 minutes.","Preheat the oven to 400°F. Place the Wellington seam-side down on a parchment-lined baking sheet. Brush with egg wash and lightly score the top.","Bake 40–45 minutes, until the pastry is golden and the internal temperature reaches 125–130°F for medium-rare.","Rest 10 minutes before slicing into thick portions."]},
{num:14,cat:"Chicken & Poultry",title:"Chicken Parmesan",meta:"Prep 20 min · Cook 25 min · Total 45 min · Serves 4",
 ing:["4 boneless, skinless chicken breasts","Salt and black pepper","1 cup all-purpose flour","2 eggs, beaten","1½ cups breadcrumbs or panko","½ cup grated Parmesan cheese","1 tsp Italian seasoning","½ cup olive oil, for frying","2 cups marinara sauce","1½ cups shredded mozzarella","Fresh basil, for garnish"],
 dir:["Preheat the oven to 425°F. Halve each chicken breast horizontally and pound to an even thickness. Season with salt and pepper.","Set up three bowls: flour; beaten eggs; and breadcrumbs mixed with Parmesan and Italian seasoning.","Dredge each cutlet in flour, then egg, then the breadcrumb mixture, pressing to coat.","Heat the olive oil in a skillet over medium-high. Fry the cutlets 2–3 minutes per side until golden. Drain on paper towels.","Spread a little marinara in a baking dish. Add the cutlets and top each with marinara and mozzarella.","Bake 15–20 minutes until the cheese is melted and bubbling and the chicken reaches 165°F.","Garnish with fresh basil and serve over pasta if desired."]},
{num:15,cat:"Pasta & Noodles",title:"Fettuccine Alfredo with Chicken",meta:"Prep 15 min · Cook 20 min · Total 35 min · Serves 4",
 ing:["12 oz fettuccine","2 boneless, skinless chicken breasts","Salt and black pepper","2 tbsp olive oil","6 tbsp butter","4 cloves garlic, minced","1½ cups heavy cream","1½ cups grated Parmesan cheese","¼ tsp ground nutmeg (optional)","Fresh parsley, chopped, for garnish"],
 dir:["Bring a large pot of salted water to a boil. Cook the fettuccine according to package instructions; reserve ½ cup pasta water, then drain.","Season the chicken with salt and pepper. Heat olive oil in a skillet over medium-high and cook 5–6 minutes per side until cooked through (165°F). Rest, then slice.","In the same skillet, melt the butter over medium heat. Add the garlic and cook until fragrant, about 1 minute.","Pour in the heavy cream and bring to a gentle simmer. Whisk in the Parmesan until smooth and the sauce thickens, 3–4 minutes. Add nutmeg and season. Loosen with reserved pasta water as needed.","Toss the fettuccine in the sauce. Top with the sliced chicken and garnish with parsley."]},
{num:16,cat:"Pasta & Noodles",title:"Beef Bolognese",meta:"Prep 20 min · Cook 2 hr · Total 2 hr 20 min · Serves 6",
 ing:["2 tbsp olive oil","1 onion, finely diced","1 carrot, finely diced","1 celery stalk, finely diced","3 cloves garlic, minced","1½ lb ground beef (or beef-and-pork blend)","½ cup whole milk","1 cup dry red wine","1 (28 oz) can crushed tomatoes","2 tbsp tomato paste","1 cup beef broth","1 bay leaf","Salt and black pepper","1 lb tagliatelle or pappardelle","Grated Parmesan, for serving"],
 dir:["Heat the olive oil in a heavy pot or Dutch oven over medium heat. Add the onion, carrot, and celery and cook until softened, 6–8 minutes. Add the garlic and cook 1 minute more.","Increase the heat to medium-high, add the ground beef, and cook, breaking it up, until browned.","Pour in the milk and simmer until mostly absorbed. Add the red wine and simmer until reduced by half.","Stir in the crushed tomatoes, tomato paste, beef broth, and bay leaf. Season with salt and pepper.","Reduce the heat to low and simmer gently, uncovered, for 1½–2 hours, stirring occasionally, until rich and thickened. Add a splash of broth or water if it gets too dry.","Cook the pasta in salted water until al dente; drain. Toss with the sauce.","Serve topped with grated Parmesan."]},
{num:17,cat:"Drinks",title:"Cucumber Gimlet",meta:"Prep 5 min · Total 5 min · Serves 1",source:"Adapted from Ocean Prime (ocean-prime.com)",
 ing:["1½ oz Bombay Sapphire gin","1 oz fresh lime juice","1 oz simple syrup","4–5 cucumber slices, plus a cucumber ribbon for garnish"],
 dir:["Fill a highball glass with ice.","Add the cucumber slices, lime juice, and simple syrup to a shaker. Muddle with about 3 ice cubes until the cucumber is pureed.","Add the gin and enough ice to fill the shaker halfway.","Shake gently, just to combine.","Strain into the iced glass and garnish with a cucumber ribbon."]},
{num:18,cat:"Pasta & Noodles",title:"Goulash",meta:"Prep 15 min · Cook 45 min · Serves 6",
 ing:["1 lb ground meat","1 medium onion","1 green pepper","1 (28 oz) can petite diced tomatoes","1 (15 oz) can tomato sauce","Salt and pepper, to taste","Nature’s Seasoning","A little bit of allspice","1 teaspoon garlic","½ of a 16 oz box of macaroni","Oil, for sautéing"],
 dir:["Sauté the onion and green pepper in oil, then add the ground meat and brown.","Drain the fat out. Add the tomato sauce and petite diced tomatoes. Salt and pepper to your taste.","Add the garlic, allspice, and Nature’s Seasoning.","Cook the macaroni according to the directions on the box (use more macaroni if you like). Drain and add to the sauce.","Let simmer for 30–45 minutes."]},
{num:19,cat:"Breakfast & Brunch",title:"Whole-Wheat Pancakes",meta:"Prep 30 min · Serves 12",source:"From Sherrie’s recipe card",
 ing:["4 cups buttermilk","½ teaspoon salt","4 tablespoons oil","2 teaspoons baking soda","2 cups whole-wheat pastry flour (about)","Eggs and sugar, if desired"],
 dir:["Use enough flour to make the correct consistency.","In a large bowl, whisk together the whole-wheat pastry flour, salt, and baking soda (add sugar here if using).","In another bowl, whisk the buttermilk and oil (and eggs, if using).","Combine the wet and dry ingredients, stirring just until mixed. Add a little more flour as needed so the batter is pourable but not runny.","Heat a lightly greased griddle or skillet over medium heat. Pour about ¼ cup of batter per pancake.","Cook until bubbles form on the surface and the edges look set, then flip and cook until golden on the other side.","Serve warm."]},
{num:20,cat:"Beef & Pork",title:"Huevos Rotos with Ibérico Secreto Steak",meta:"Easy · 30 min · Serves 4 · Main",source:CG,
 note:"Huevos rotos, or “broken eggs,” is a popular dish in Spain and can be served with any toppings and meat you fancy. Fry the eggs as you normally would, leaving them a bit runny so they create a thick sauce to coat the potatoes and secreto.",
 ing:["1 Campo Grande Secreto","4 large potatoes, cut into thick matchsticks","Extra-virgin olive oil","8 eggs","Salt (to taste)","Black pepper (to taste)"],
 dir:["Heat olive oil in a large cast iron skillet and fry the potatoes until soft on the inside but crispy on the outside. Remove from the oil and set aside. Remove most of the oil from the pan.","Season the Secreto with salt and pepper and cook in the same skillet for 3 minutes on each side. Remove from the pan and let rest.","Fry the eggs in the pan, leaving the yolks slightly runny.","Slice the Secreto and serve over the potatoes, topping with the eggs.","Cut up the potatoes, meat, and eggs, mixing each ingredient together to create a delicious potato-y, eggy, porky mess (this is where the eggs become “roto”). ¡Buen provecho!"]},
{num:21,cat:"Desserts & Sweets",title:"Kentucky Bourbon Cake",meta:"Prep 55 min · Serves 16",source:"Recipe by Loraine",
 note:"Really good for Thanksgiving or Christmas.",
 ing:["1 box Duncan Hines Yellow Cake Mix","1 package instant Vanilla Pudding mix","4 eggs","½ cup cooking oil","¼ cup Kentucky bourbon","¾ cup water","For the topping:","½ cup bourbon","¼ cup butter","1½ cups confectioners’ sugar"],
 dir:["Mix the ingredients together at moderate speed for 5 to 10 minutes. Pour into a 10-inch tube or Bundt pan.","Bake in a 350°F oven for approximately 40 minutes.","For the topping:","Mix the bourbon, butter, and confectioners’ sugar together until desired consistency.","Drizzle or spread the topping over the cake."]},
{num:22,cat:"Seafood",title:"Broiled Lobster Tails with Garlic Butter",meta:"Prep 15 min · Cook 10 min · Serves 4",
 ing:["4 lobster tails (5–6 oz each)","6 tbsp butter, melted","4 cloves garlic, minced","1 tbsp fresh lemon juice","1 tsp lemon zest","½ tsp paprika","Salt and black pepper, to taste","1 tbsp fresh parsley, chopped","Lemon wedges, for serving"],
 dir:["Position an oven rack about 6 inches below the broiler and preheat the broiler to high.","Butterfly the tails: using kitchen shears, cut down the top of each shell to the base of the tail, leaving the fin intact. Gently pull the shell open and lift the meat to rest on top of the shell.","In a small bowl, combine the melted butter, garlic, lemon juice, lemon zest, and paprika. Season with salt and pepper.","Arrange the tails on a baking sheet and brush generously with about half of the garlic butter.","Broil for 8–10 minutes, until the meat is opaque and reaches an internal temperature of 140°F, brushing once more with butter halfway through.","Garnish with parsley and serve with the remaining garlic butter and lemon wedges."]},
{num:23,cat:"Seafood",title:"Garlic Butter Shrimp Scampi",meta:"Prep 10 min · Cook 10 min · Total 20 min · Serves 4",
 ing:["1 lb large shrimp, peeled and deveined","Salt and black pepper","3 tbsp butter","2 tbsp olive oil","5 cloves garlic, minced","¼ tsp red pepper flakes","½ cup dry white wine (or chicken broth)","3 tbsp fresh lemon juice","8 oz linguine (optional)","¼ cup fresh parsley, chopped"],
 dir:["If serving over pasta, cook the linguine in salted water until al dente; reserve ½ cup pasta water, then drain.","Pat the shrimp dry and season with salt and pepper.","Heat 1 tbsp of the butter and the olive oil in a large skillet over medium-high. Add the shrimp in a single layer and cook 1–2 minutes per side until just pink. Remove and set aside.","Reduce the heat to medium. Add the garlic and red pepper flakes and cook until fragrant, about 1 minute.","Pour in the white wine and lemon juice, scraping up any browned bits. Simmer 2–3 minutes until slightly reduced.","Stir in the remaining 2 tbsp butter until melted, then return the shrimp to the pan and toss to coat.","Add the parsley (and toss with the pasta, loosening with reserved pasta water, if using). Serve immediately."]},
{num:24,cat:"Seafood",title:"Pan-Seared Red Snapper with Lemon Butter Sauce",meta:"Prep 10 min · Cook 10 min · Serves 4",
 ing:["4 red snapper fillets (about 6 oz each), skin on","Salt and black pepper","2 tbsp olive oil","3 tbsp butter","2 cloves garlic, minced","2 tbsp fresh lemon juice","1 tbsp capers, drained (optional)","2 tbsp fresh parsley, chopped","Lemon wedges, for serving"],
 dir:["Pat the fillets dry and season both sides with salt and pepper. Lightly score the skin to keep the fillets from curling.","Heat the olive oil in a large skillet over medium-high until shimmering.","Place the fillets skin-side down, pressing gently with a spatula for the first 30 seconds. Sear 3–4 minutes until the skin is crisp.","Flip and cook 2–3 minutes more, until the fish is opaque and flakes easily. Transfer to plates.","Reduce the heat to medium. Add the butter and garlic and cook until fragrant, about 1 minute, then stir in the lemon juice and capers.","Spoon the lemon butter sauce over the fish, garnish with parsley, and serve with lemon wedges."]},
{num:25,cat:"Soups & Salads",title:"Columbia “1905” Salad",meta:"Prep 15 min · Makes 2 entrée or 4 side salads",source:"Columbia Restaurant, Tampa (columbiarestaurant.com)",
 note:"Florida’s most famous salad, created by waiter Tony Noriega in the 1940s. For best results, make the dressing 1–2 days ahead.",
 ing:["For the salad:","4 cups iceberg lettuce, broken into 1½-inch pieces","1 ripe tomato, cut into eighths","½ cup baked ham, julienned (may substitute turkey or shrimp)","½ cup Swiss cheese, julienned","½ cup green Spanish olives","¼ cup grated Romano cheese","2 tbsp Lea & Perrins Worcestershire sauce","Juice of 1 lemon","1 cup “1905” dressing (below)","For the “1905” dressing:","½ cup extra-virgin Spanish olive oil","4 garlic cloves, minced","2 tsp dried oregano","⅛ cup white wine vinegar","Salt and pepper, to taste"],
 dir:["For the dressing:","Mix the olive oil, garlic, and oregano in a bowl. Stir in the vinegar and season with salt and pepper. For best results, prepare 1–2 days in advance and refrigerate.","For the salad:","Combine the lettuce, tomato, ham, Swiss cheese, and olives in a large salad bowl.","Just before serving, add 1 cup of the “1905” dressing, the Romano cheese, Worcestershire sauce, and the juice of 1 lemon.","Toss well and serve immediately."]},
{num:26,cat:"Soups & Salads",title:"Wedge Salad with Blue Cheese & Bacon",meta:"Prep 20 min · Serves 4",
 ing:["For the salad:","1 head iceberg lettuce, cut into 4 wedges","6 slices bacon, cooked crisp and crumbled","1 cup cherry tomatoes, halved","½ cup crumbled blue cheese","2 tbsp fresh chives, chopped","For the blue cheese dressing:","½ cup mayonnaise","½ cup sour cream","4 oz blue cheese, crumbled","1 tbsp fresh lemon juice","1 tsp Worcestershire sauce","Salt and black pepper, to taste","Milk or buttermilk, to thin (optional)"],
 dir:["For the dressing:","Whisk together the mayonnaise, sour cream, lemon juice, and Worcestershire. Stir in the blue cheese, mashing some and leaving some chunks. Season with salt and pepper; thin with a splash of milk if needed.","For the salad:","Place each iceberg wedge cut-side up on a chilled plate.","Spoon the blue cheese dressing generously over each wedge.","Top with the crumbled bacon, cherry tomatoes, extra blue cheese crumbles, and chives. Serve cold."]},
{num:27,cat:"Chicken & Poultry",title:"Chicken Paillard with Arugula & Lemon Truffle Vinaigrette",meta:"Prep 15 min · Cook 10 min · Serves 4",source:"Inspired by Mad Dogs & Englishmen, Tampa (maddogs.com)",
 ing:["For the chicken:","4 boneless, skinless chicken breasts","Salt and black pepper","2 tbsp olive oil","For the lemon truffle vinaigrette:","3 tbsp extra-virgin olive oil","1 tbsp fresh lemon juice","1 tsp Dijon mustard","½ tsp truffle oil (or to taste)","Salt and black pepper","To serve:","4 cups arugula","½ cup shaved Parmesan","½ cup croutons (toasty bits)","Garlic aioli and kettle chips"],
 dir:["Halve each chicken breast horizontally, then pound between sheets of plastic wrap to an even ¼-inch thickness. Season both sides with salt and pepper.","Whisk together the olive oil, lemon juice, Dijon, and truffle oil. Season with salt and pepper and set aside.","Heat the 2 tbsp olive oil in a large skillet over medium-high. Sear the chicken 2–3 minutes per side until golden and cooked through (165°F). Transfer to plates.","Toss the arugula with most of the vinaigrette and pile on top of each chicken paillard.","Top with shaved Parmesan and croutons, drizzle with the remaining vinaigrette, and serve with garlic aioli and crispy chips."]},
{num:28,cat:"Appetizers & Starters",title:"Bruschetta al Pomodoro",meta:"Italian · Prep 15 min · Cook 5 min · Serves 6",
 ing:["1 baguette or ciabatta, sliced ½-inch thick","4 ripe tomatoes, diced","2 cloves garlic (1 minced, 1 whole for rubbing)","8 fresh basil leaves, thinly sliced","3 tbsp extra-virgin olive oil, plus more for brushing","1 tsp balsamic vinegar","Salt and black pepper, to taste"],
 dir:["Combine the diced tomatoes, minced garlic, basil, 3 tbsp olive oil, and balsamic in a bowl. Season with salt and pepper and let sit 10 minutes.","Brush the bread slices with olive oil and toast or grill until golden on both sides.","Rub each warm slice with the cut side of the whole garlic clove.","Spoon the tomato mixture onto the toasts just before serving so the bread stays crisp."]},
{num:29,cat:"Appetizers & Starters",title:"Classic Shrimp Cocktail",meta:"Seafood · Prep 15 min · Cook 5 min · Serves 6",
 ing:["For the shrimp:","1½ lb large shrimp (16–20 count), peeled and deveined, tails on","1 lemon, halved","1 bay leaf","1 tbsp salt","For the cocktail sauce:","½ cup ketchup","2–3 tbsp prepared horseradish","1 tbsp fresh lemon juice","1 tsp Worcestershire sauce","A few dashes hot sauce (optional)"],
 dir:["Bring a large pot of water to a boil with the lemon halves, bay leaf, and salt.","Add the shrimp and cook 2–3 minutes, just until pink and opaque. Drain and immediately plunge into an ice bath to stop the cooking.","Whisk together the ketchup, horseradish, lemon juice, Worcestershire, and hot sauce. Chill.","Drain the shrimp well, pat dry, and arrange around a bowl of the cocktail sauce. Serve cold."]},
{num:30,cat:"Appetizers & Starters",title:"Saganaki (Greek Fried Cheese)",meta:"Greek · Prep 5 min · Cook 5 min · Serves 4",
 ing:["8 oz kefalograviera, kasseri, or halloumi, in a ½-inch-thick slab","¼ cup flour, for dredging","2 tbsp olive oil","1 lemon, cut into wedges","2 tbsp brandy or ouzo (optional, for flaming)"],
 dir:["Dip the cheese slab briefly in water, then dredge in flour to coat all sides.","Heat the olive oil in a small heavy skillet over medium-high until shimmering.","Fry the cheese 1–2 minutes per side until a golden crust forms.","Optional flambé: off the heat, add the brandy and carefully ignite with a long match; once the flames die down, squeeze lemon over to extinguish. Opa!","Serve immediately with lemon wedges and crusty bread."]},
{num:31,cat:"Appetizers & Starters",title:"Fresh Guacamole",meta:"Mexican · Prep 15 min · Serves 6",
 ing:["3 ripe avocados","½ small white onion, finely diced","1 Roma tomato, seeded and diced","1–2 serrano or jalapeño peppers, minced","¼ cup fresh cilantro, chopped","2 tbsp fresh lime juice","½ tsp salt, plus more to taste","Tortilla chips, for serving"],
 dir:["Halve and pit the avocados, scoop the flesh into a bowl, and mash to your preferred texture.","Stir in the onion, tomato, chili, cilantro, and lime juice.","Season with salt and adjust the lime to taste.","Serve right away with tortilla chips. If holding, press plastic wrap directly onto the surface to prevent browning."]},
{num:32,cat:"Appetizers & Starters",title:"Oysters Rockefeller",meta:"Steakhouse · Prep 20 min · Cook 12 min · Serves 4",
 ing:["24 fresh oysters on the half shell","4 tbsp butter","2 cups baby spinach, finely chopped","2 shallots, minced","2 cloves garlic, minced","¼ cup fresh parsley, chopped","2 tbsp Pernod or anise liqueur (optional)","¼ cup breadcrumbs","¼ cup grated Parmesan","Rock salt, for baking","Lemon wedges, for serving"],
 dir:["Preheat the oven to 450°F. Spread a layer of rock salt on a baking sheet to steady the shells.","Melt the butter in a skillet over medium heat. Add the shallots and garlic and cook until soft, about 2 minutes.","Add the spinach and parsley and cook until wilted. Stir in the Pernod (if using) and cook 1 minute more. Season with salt and pepper and let cool slightly.","Nestle the oysters in their shells on the rock salt and top each with a spoonful of the spinach mixture.","Combine the breadcrumbs and Parmesan and sprinkle over the top.","Bake 10–12 minutes, until bubbling and golden. Serve hot with lemon wedges."]},
{num:33,cat:"Desserts & Sweets",title:"Congo Bars",meta:"Bake 350°F · 20–30 min · Makes one 16½×10½ pan",
 note:"The larger the pan, the thinner the bars will be.",
 ing:["2⅔ cups (or 1 lb) brown sugar","¾ cup (1½ sticks) butter or margarine","3 eggs","1 tsp vanilla","2⅔ cups flour","2 tsp baking powder","½ tsp salt","1 (12 oz) package chocolate morsels","1 cup nut meats (optional)"],
 dir:["Cream the sugar and butter together. Add the eggs one at a time, then add the vanilla, flour, baking powder, and salt.","Stir in the chocolate chips and nuts last.","Spread into a greased 16½×10½-inch pan.","Bake at 350°F for 20 to 30 minutes."]}
];

// ---- State ----
function loadUser(){ try{ return JSON.parse(localStorage.getItem(STORAGE_KEY)) || []; }catch(e){ return []; } }
function saveUser(arr){ localStorage.setItem(STORAGE_KEY, JSON.stringify(arr)); }
function allRecipes(){
  const user = loadUser();
  return SEED.concat(user).slice().sort((a,b)=>a.num-b.num);
}
function nextNum(){
  const all = allRecipes();
  return all.length ? Math.max(...all.map(r=>r.num))+1 : 1;
}

// ---- Rendering ----
function esc(s){ return (s||"").replace(/[&<>"]/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c])); }
function isSub(line){ return /:\s*$/.test(line.trim()); }

function renderIndex(recipes){
  const box = document.getElementById("indexBody");
  let html = "";
  CATEGORIES.forEach(cat=>{
    const items = recipes.filter(r=>r.cat===cat).sort((a,b)=>a.num-b.num);
    html += '<div class="cat-block"><div class="cat-name">'+esc(cat)+'</div>';
    if(!items.length){ html += '<div class="cat-empty">— no recipes yet —</div></div>'; return; }
    html += '<ol>';
    items.forEach(r=>{ html += '<li data-go="r'+r.num+'"><span>'+esc(r.title)+(r.user?'<span class="badge-new">ADDED</span>':'')+'</span><span class="num">No. '+r.num+'</span></li>'; });
    html += '</ol></div>';
  });
  box.innerHTML = html;
  box.querySelectorAll("li[data-go]").forEach(li=>{
    li.onclick = ()=>{ const el=document.getElementById(li.dataset.go); if(el){ el.scrollIntoView({behavior:"smooth",block:"start"}); el.style.transition="background .2s"; el.style.background="#fdf6ec"; setTimeout(()=>el.style.background="#fff",900);} };
  });
}

function renderRecipe(r){
  let h = '<div class="recipe" id="r'+r.num+'">';
  h += '<div class="rnum">Recipe No. '+r.num+(r.user?' <span class="badge-new">ADDED</span>':'')+'</div>';
  h += '<h3>'+esc(r.title)+'</h3>';
  h += '<div class="cat-tag">'+esc(r.cat)+'</div>';
  if(r.meta) h += '<div class="meta">'+esc(r.meta)+'</div>';
  if(r.source) h += '<div class="source">'+esc(r.source)+'</div>';
  if(r.note) h += '<p class="note">'+esc(r.note)+'</p>';
  h += '<div class="cols"><div><h4>Ingredients</h4><ul class="ing">';
  r.ing.forEach(i=>{ h += '<li'+(isSub(i)?' class="subhead"':'')+'>'+esc(i)+'</li>'; });
  h += '</ul></div><div><h4>Directions</h4><ol class="dir">';
  r.dir.forEach(d=>{ h += '<li'+(isSub(d)?' class="subhead"':'')+'>'+esc(d)+'</li>'; });
  h += '</ol></div></div></div>';
  return h;
}

function applyFilter(){
  const q = document.getElementById("search").value.trim().toLowerCase();
  const cat = document.getElementById("catFilter").value;
  let recipes = allRecipes();
  let list = recipes.filter(r=>{
    if(cat && r.cat!==cat) return false;
    if(!q) return true;
    const hay = (r.title+" "+r.cat+" "+r.ing.join(" ")+" "+r.dir.join(" ")).toLowerCase();
    return hay.includes(q);
  });
  const target = document.getElementById("recipeList");
  target.innerHTML = list.length ? list.map(renderRecipe).join("") : '<div class="empty-state">No recipes match your search.</div>';
  renderIndex(recipes);
  document.getElementById("countPill").textContent = recipes.length + " recipe" + (recipes.length===1?"":"s");
}

// ---- Add recipe ----
const modalBg = document.getElementById("modalBg");
function openModal(){
  document.getElementById("f_title").value="";
  document.getElementById("f_meta").value="";
  document.getElementById("f_source").value="";
  document.getElementById("f_ing").value="";
  document.getElementById("f_dir").value="";
  modalBg.classList.add("open");
}
function closeModal(){ modalBg.classList.remove("open"); }

function saveRecipe(){
  const title = document.getElementById("f_title").value.trim();
  const ing = document.getElementById("f_ing").value.split("\n").map(s=>s.trim()).filter(Boolean);
  const dir = document.getElementById("f_dir").value.split("\n").map(s=>s.trim()).filter(Boolean);
  if(!title){ alert("Please give the recipe a name."); return; }
  if(!ing.length && !dir.length){ alert("Add at least some ingredients or directions."); return; }
  const rec = {
    num: nextNum(),
    cat: document.getElementById("f_cat").value,
    title: title,
    meta: document.getElementById("f_meta").value.trim(),
    source: document.getElementById("f_source").value.trim(),
    ing: ing, dir: dir, user: true
  };
  const user = loadUser();
  user.push(rec);
  saveUser(user);
  closeModal();
  applyFilter();
  setTimeout(()=>{ const el=document.getElementById("r"+rec.num); if(el){ el.scrollIntoView({behavior:"smooth",block:"start"}); el.style.background="#f0f8f1"; setTimeout(()=>el.style.background="#fff",1200);} },120);
}

function resetAll(){
  if(confirm("Remove the recipes you've added and restore the original collection?")){
    localStorage.removeItem(STORAGE_KEY);
    applyFilter();
  }
}

// ---- Init ----
function init(){
  const cf = document.getElementById("catFilter");
  const fc = document.getElementById("f_cat");
  CATEGORIES.forEach(c=>{
    cf.insertAdjacentHTML("beforeend",'<option value="'+esc(c)+'">'+esc(c)+'</option>');
    fc.insertAdjacentHTML("beforeend",'<option value="'+esc(c)+'">'+esc(c)+'</option>');
  });
  fc.value = "Beef & Pork";
  document.getElementById("search").addEventListener("input", applyFilter);
  document.getElementById("catFilter").addEventListener("change", applyFilter);
  document.getElementById("addBtn").addEventListener("click", openModal);
  document.getElementById("cancelBtn").addEventListener("click", closeModal);
  document.getElementById("saveBtn").addEventListener("click", saveRecipe);
  document.getElementById("resetBtn").addEventListener("click", resetAll);
  modalBg.addEventListener("click", e=>{ if(e.target===modalBg) closeModal(); });
  applyFilter();
}
init();
</script>
</body>
</html>
