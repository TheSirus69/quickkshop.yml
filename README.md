# QuickkShop Configuration Guide

**Welcome!** This guide will help you edit the shop items for our server. Don't worry if you're not tech-savvy - we'll walk through everything step by step.

## Table of Contents
- [How to Edit on GitHub (Start Here!)](#how-to-edit-on-github-start-here)
- [Understanding the Shop File](#understanding-the-shop-file)
- [How to Change Prices](#how-to-change-prices)
- [How to Add New Items](#how-to-add-new-items)
- [How to Add Color to Names](#how-to-add-color-to-names)
- [Understanding Slots (Positions)](#understanding-slots-positions)
- [Common Mistakes to Avoid](#common-mistakes-to-avoid)
- [Reference: All Settings Explained](#reference-all-settings-explained)

---

## How to Edit on GitHub (Start Here!)

If you're new to GitHub, follow these simple steps:

### Step 1: Find the File
1. Go to the GitHub repository (the link your admin gave you)
2. Click on the file called `shop.yml`

### Step 2: Edit the File
1. Click the pencil icon (Edit button) in the top-right corner
2. Make your changes to the file
3. Be careful with spacing - don't delete spaces at the start of lines!

### Step 3: Save Your Changes
1. Scroll down to the bottom of the page
2. In the "Commit changes" box, type a short description like "Updated diamond prices" or "Added new farming items"
3. Click the green "Commit changes" button

### Step 4: Done!
Your changes are saved! An admin will review and apply them to the server.

### Important GitHub Tips
- Each line's spacing matters - don't add or remove spaces at the start of lines
- If you make a mistake, don't panic! Admins can undo changes
- Always describe what you changed in the commit message
- Preview your changes before saving if possible

---

## Understanding the Shop File

Think of the shop like a store with different sections:
- **Categories** = Store sections (like "Farming", "Ores", "Blocks")
- **Items** = Individual products in each section (like "Diamond", "Wheat Seeds")

### What Does the File Look Like?

Here's a simple example:

```yaml
categories:
  ores:                          # This is the section ID
    name: "&b&lOres & Ingots"   # This is what players see
    icon: "DIAMOND"              # This is the picture shown
    slot: 10                     # This is where it appears in the menu
    items:                       # Items in this section start here
      diamond:                   # This is the item ID
        type: "NORMAL"
        material: "DIAMOND"
        name: "&bDiamond"
        buy-price: 2000.0        # Players pay this to BUY
        sell-price: 15.0         # Players get this to SELL
        slot: 12
        amount: 64
```

---

## How to Change Prices

This is the most common task! Here's how:

### Example: Making Diamonds More Expensive

**Before:**
```yaml
diamond:
  type: "NORMAL"
  material: "DIAMOND"
  name: "&bDiamond"
  lore: []
  buy-price: 2000.0        # Current buy price
  sell-price: 15.0         # Current sell price
  slot: 12
  amount: 64
```

**After:**
```yaml
diamond:
  type: "NORMAL"
  material: "DIAMOND"
  name: "&bDiamond"
  lore: []
  buy-price: 3500.0        # New buy price - more expensive!
  sell-price: 20.0         # New sell price - players get more!
  slot: 12
  amount: 64
```

### Remember
- **buy-price** = What players PAY to get it from the shop
- **sell-price** = What players GET when selling to the shop
- Use `-1` for sell-price if you don't want players to sell it

### Quick Price Changes
1. Find the item in the file (use Ctrl+F to search)
2. Look for `buy-price:` or `sell-price:`
3. Change the number
4. Save (commit) your changes

---

## How to Add Color to Names

Want to make items look prettier? Use color codes!

### Simple Color Guide

Just add `&` followed by a letter before the text:

| What to Type | Color You Get |
|--------------|---------------|
| `&a` | Green |
| `&b` | Aqua (Light Blue) |
| `&c` | Red |
| `&e` | Yellow |
| `&6` | Gold/Orange |
| `&d` | Pink |
| `&5` | Purple |
| `&f` | White |
| `&l` | Make text BOLD |

### Examples You Can Copy

```yaml
name: "&aGreen Apple"         # Green colored name
name: "&bDiamond"             # Aqua/light blue
name: "&c&lREDSTONE"          # Red and bold
name: "&6Gold Ingot"          # Gold/orange color
name: "&d&lRARE ITEM"         # Pink and bold
```

### How to Use It
1. Find the `name:` line for your item
2. Add the color code right after the quote mark
3. Example: Change `name: "Diamond"` to `name: "&bDiamond"`

---

## Understanding Slots (Positions)

Slots determine where items appear in the shop menu. Think of it like a grid:

```
Row 1:   0   1   2   3   4   5   6   7   8
Row 2:   9  10  11  12  13  14  15  16  17
Row 3:  18  19  20  21  22  23  24  25  26
Row 4:  27  28  29  30  31  32  33  34  35
Row 5:  36  37  38  39  40  41  42  43  44
Row 6:  45  46  47  48  49  50  51  52  53
```

### Easy Slot Numbers to Remember
- **Top left corner** = 0
- **Top right corner** = 8
- **Middle of screen** = 22
- **Bottom left** = 45
- **Bottom right** = 53

### Tips
- Don't use the same slot number twice in the same category!
- Popular spots: 10-16, 19-25, 28-34 (the middle area)
- Leave some empty slots for a cleaner look

---

## How to Add New Items

Want to add a new item to the shop? Follow these steps:

### Step-by-Step Guide

**Step 1:** Find the category where you want to add the item
- Example: To add an item to the Farming section, search for `farming:`

**Step 2:** Scroll down to the last item in that category

**Step 3:** Copy an existing item and paste it below (keep the same spacing!)

**Step 4:** Change the details to match your new item

### Full Example: Adding Copper Ore to Ores

**Find this section:**
```yaml
  ores:
    name: "&b&lOres & Ingots"
    icon: "DIAMOND"
    slot: 10
    items:
      # ... other items here ...

      amethyst_shard:          # Last item in the list
        type: "NORMAL"
        material: "AMETHYST_SHARD"
        name: "&dAmethyst Shard"
        lore: []
        buy-price: 350.0
        sell-price: 3.5
        slot: 28
        amount: 64
```

**Add your new item below it:**
```yaml
      copper_ore:              # Your new item name (no spaces!)
        type: "NORMAL"
        material: "COPPER_ORE" # The Minecraft item name
        name: "&6Copper Ore"   # What players will see
        lore: []               # Leave empty or add description
        buy-price: 100.0       # What players pay
        sell-price: 5.0        # What players get for selling
        slot: 29               # Pick an empty slot number
        amount: 64             # How many per stack
```

### Important Tips for Adding Items
1. **Spacing matters!** Make sure your new item lines up with the others
2. **Use a unique slot number** - don't use a slot that's already taken
3. **Material names** must match Minecraft's exact names (like "DIAMOND", "IRON_ORE", "WHEAT")
4. **No spaces** in the item ID (use `copper_ore` not `copper ore`)
5. Find Minecraft material names here: https://minecraft.wiki

### Quick Copy Template

Copy this and fill in the blanks:

```yaml
      your_item_name:
        type: "NORMAL"
        material: "MATERIAL_NAME"
        name: "&fItem Display Name"
        lore: []
        buy-price: 100.0
        sell-price: 10.0
        slot: 10
        amount: 64
```

---

## Important Notes

### Price Settings
- **buy-price**: What players PAY to get the item from the shop
- **sell-price**: What players RECEIVE when selling to the shop
- Set `sell-price: -1` to disable selling (buy-only items)
- Prices are in your server's economy currency

### Material Names
- Use valid Minecraft material IDs (e.g., `DIAMOND`, `IRON_INGOT`, `OAK_LOG`)
- Material names are CASE SENSITIVE
- Find valid materials at: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html

### Lore
- Can be empty: `lore: []`
- Or contain multiple lines:
  ```yaml
  lore:
    - "&7Line 1"
    - "&7Line 2"
    - "&aLine 3"
  ```

### Indentation
- **CRITICAL**: YAML is indentation-sensitive
- Use 2 spaces for each level of indentation
- Never use tabs
- Keep alignment consistent

### Spawners
- Only works if you have AxSpawners plugin installed
- Use `axspawner-id` to specify the mob type
- Valid mob types: zombie, skeleton, creeper, spider, enderman, blaze, etc.

### Common Mistakes
- Forgetting quotes around color codes: Use `"&bBlue"` not `&bBlue`
- Wrong indentation (use 2 spaces consistently)
- Invalid material names
- Missing required fields
- Using tabs instead of spaces
- Duplicate slot numbers (items will overlap)
- Typos in property names

---

## Need Help?

If you encounter issues:
1. Check console for error messages
2. Verify your YAML syntax at: https://www.yamllint.com/
3. Make sure all material names are valid
4. Ensure proper indentation (2 spaces per level)
5. Contact the server administrator

---

**Last Updated**: 2025
**Plugin**: QuickkShop
****
