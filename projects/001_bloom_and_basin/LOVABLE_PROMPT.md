# Lovable.dev Build Prompt - Bloom & Basin

**COPY EVERYTHING BELOW THIS LINE AND PASTE INTO LOVABLE.DEV**

---

# Build a 5-Page Website for Bloom & Basin

Build a professional, modern website for **Bloom & Basin**, a Phoenix-based plant shop and landscaping company specializing in desert-adapted plants, succulents, and water-wise landscape design.

## Design Style & Brand Identity

**Visual Style:**
- Modern desert aesthetic - clean lines, warm earth tones, natural textures
- Sophisticated but approachable (not pretentious)
- Lots of white space, organic shapes, plant-inspired elements
- Premium feel with warm, inviting personality

**Color Palette:**

Primary Colors:
- **Sage Green** (Primary): `#7A9B76` - Use for logo, primary CTAs, headers, active navigation
- **Terracotta** (Secondary): `#C07855` - Use for accents, hover states, secondary CTAs
- **Sand Cream** (Accent): `#E8DCC4` - Use for background sections, cards

Neutral Colors:
- **Warm Charcoal** (Text): `#3A3635` - Use for body text, headings
- **Warm Gray** (Background): `#F5F3F0` - Use for page backgrounds, subtle sections
- **White**: `#FFFFFF` - Use for clean backgrounds, text on dark

CSS Variables:
```css
:root {
  --color-primary: #7A9B76;
  --color-secondary: #C07855;
  --color-accent: #E8DCC4;
  --color-dark: #3A3635;
  --color-gray-light: #F5F3F0;
  --color-white: #FFFFFF;
}
```

**Typography:**

Heading Font: **Crimson Pro** (Google Fonts)
- Weights: 600 (Semi-Bold), 700 (Bold)
- Use for: H1, H2, H3, H4, hero text
- Import: `https://fonts.googleapis.com/css2?family=Crimson+Pro:wght@600;700&display=swap`

Body Font: **Inter** (Google Fonts)
- Weights: 400 (Regular), 500 (Medium), 600 (Semi-Bold)
- Use for: Body text, navigation, buttons, labels
- Import: `https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap`

Typography Scale:
- H1: 3.5rem (56px), Crimson Pro 600, line-height 1.2
- H2: 2.5rem (40px), Crimson Pro 600, line-height 1.3
- H3: 1.75rem (28px), Crimson Pro 600, line-height 1.4
- Body: 1rem (16px), Inter 400, line-height 1.7
- Body Large: 1.25rem (20px), Inter 400, line-height 1.7

**Logo:**
Since we don't have a visual logo file yet, create a simple text-based logo:
- Text: "Bloom & Basin"
- Font: Crimson Pro Semi-Bold
- Icon: Use a simple plant emoji 🌵 or create a minimalist succulent icon in the Sage Green color
- Layout: Icon on left, text on right

**Button Styles:**

Primary Button:
- Background: Sage Green (#7A9B76)
- Text: White
- Padding: 0.75rem 2rem
- Border-radius: 4px
- Font: Inter Medium (500)
- Hover: Darker sage (#6A8A66)

Secondary Button:
- Background: Transparent
- Border: 2px solid Sage Green
- Text: Sage Green
- Hover: Background fills with Sage Green, text turns white

**Reference Sites for Inspiration:**
- The Sill (thesill.com) - Clean plant shop aesthetic
- Leaf & Clay (leafandclay.co) - Desert/succulent focus
- Terrain (shopterrain.com) - Earthy, premium garden feel

---

## Website Structure - 5 Pages

1. **Homepage** (/)
2. **Shop** (/shop)
3. **Services** (/services)
4. **About** (/about)
5. **Contact** (/contact)

---

## Navigation

**Header Navigation:**
- Logo: "Bloom & Basin" (left side)
- Menu Links (right side): Home | Shop | Services | About | Contact
- Primary CTA Button: "Get a Free Quote" (Sage green button)
- Phone: (602) 555-0143 (displayed on desktop, hidden on mobile)
- Sticky header on scroll
- Mobile: Hamburger menu

**Footer:**
- Logo and tagline: "Desert-inspired greenery for your home and yard"
- Contact Info: Address, Phone, Email, Hours
- Quick Links: Shop | Services | About | Contact
- Social Media: Instagram (@bloomandbasin), Facebook (/bloomandbasinphx)
- Copyright: © 2025 Bloom & Basin. All rights reserved.

---

## PAGE 1: HOMEPAGE (/)

**Meta:**
- Title: "Bloom & Basin | Desert Plants & Landscaping in Phoenix, AZ"
- Description: "Phoenix's premier plant shop & landscaping company. Specializing in drought-tolerant plants, succulents, and water-wise landscape design. Visit our shop or get a quote today."

### Hero Section (Full-width, image background with overlay)

**Headline (H1):**
Desert-Inspired Greenery for Your Home and Yard

**Subheadline:**
Phoenix's local plant shop and landscaping experts, bringing beauty and sustainability to your space with drought-tolerant plants and water-wise design.

**CTAs:**
- Primary Button: "Get a Free Quote"
- Secondary Button: "Visit Our Shop"

**Background:** Hero image of a beautiful desert landscape with succulents and native plants (use stock imagery of Arizona desert landscaping). Add a subtle sage green overlay for text readability.

---

### Services Overview Section

**Section Headline (H2):**
Shop Plants & Transform Landscapes

**Body Text:**
Whether you're looking for the perfect succulent for your living room or a complete yard transformation, we're here to help. Our retail shop offers carefully curated desert-adapted plants, while our landscaping team designs and installs stunning outdoor spaces built for Arizona's climate.

**3 Service Cards:**

**Card 1:**
**Icon:** 🪴 (or plant icon)
**Title:** Retail Plant Shop
**Description:** Browse our collection of succulents, cacti, indoor plants, and desert-adapted greenery—plus pottery, planters, and expert care advice. Everything we carry is selected to thrive in Phoenix.

**Card 2:**
**Icon:** 🎨 (or design icon)
**Title:** Landscape Design
**Description:** Custom landscape plans that blend beauty with sustainability. We design outdoor spaces that celebrate the desert while conserving water and requiring minimal maintenance.

**Card 3:**
**Icon:** 🌱 (or installation icon)
**Title:** Installation & Maintenance
**Description:** From irrigation systems to seasonal planting, our team handles every detail. We'll bring your landscape vision to life and keep it thriving year-round.

**CTA Button:** "Explore Our Services"

**Layout:** 3-column grid on desktop, stacked on mobile. White background with subtle shadows on cards.

---

### Why Choose Us Section (Background: Warm Gray #F5F3F0)

**Section Headline (H2):**
Why Phoenix Trusts Bloom & Basin

**4 Feature Points (2x2 grid on desktop, stacked on mobile):**

**Point 1:**
**Icon/Emoji:** 🌵
**Title:** Desert Experts
**Description:** We know what thrives in Arizona's unique climate. Every plant we sell and every landscape we design is proven to flourish in the desert heat and low rainfall.

**Point 2:**
**Icon/Emoji:** 🏪
**Title:** Shop + Service
**Description:** One-stop convenience. Buy plants from our retail shop or work with our professional team for complete landscape design, installation, and ongoing care.

**Point 3:**
**Icon/Emoji:** 💧
**Title:** Water-Wise Beauty
**Description:** Gorgeous doesn't have to mean wasteful. Our focus is on sustainable, drought-tolerant landscapes that save water while looking stunning.

**Point 4:**
**Icon/Emoji:** ❤️
**Title:** Local & Passionate
**Description:** We're Phoenix locals who genuinely love what we do. When you work with us, you get personalized service from people who care about your space as much as you do.

---

### Testimonials Section (White background)

**Section Headline (H2):**
What Our Customers Say

**3 Testimonial Cards (horizontal row on desktop, stacked on mobile):**

**Testimonial 1:**
**Quote:** "Bloom & Basin transformed our backyard into an oasis. We get compliments from neighbors every week!"
**Attribution:** Sarah M., Scottsdale
**Star Rating:** ⭐⭐⭐⭐⭐

**Testimonial 2:**
**Quote:** "Finally found a plant shop that understands the desert. Everything I've bought has thrived."
**Attribution:** David L., Tempe
**Star Rating:** ⭐⭐⭐⭐⭐

**Testimonial 3:**
**Quote:** "Professional, creative, and they really listened to what we wanted. Our xeriscape is stunning."
**Attribution:** The Rodriguez Family, Phoenix
**Star Rating:** ⭐⭐⭐⭐⭐

**Design:** Light sand cream background cards with subtle shadows, centered text, large quote marks.

---

### Final CTA Section (Background: Sage Green with white text)

**Headline (H2):**
Ready to Bring Your Space to Life?

**Body Text:**
Whether you're shopping for a single plant or planning a complete landscape transformation, we're here to help. Stop by our Phoenix shop or schedule a free consultation for landscaping services.

**CTAs (centered):**
- Primary Button: "Get a Free Quote" (white button with sage green text)
- Secondary Button: "Visit Our Shop" (outlined white button)
- Phone Link: "Call Us: (602) 555-0143"

---

## PAGE 2: SHOP (/shop)

**Meta:**
- Title: "Shop Desert Plants & Succulents | Bloom & Basin Phoenix"
- Description: "Browse our curated collection of succulents, cacti, indoor plants, and pottery. All plants selected to thrive in Phoenix's desert climate. Visit us at 2847 N 7th Street."

### Hero Section

**Headline (H1):**
Plants That Thrive in the Desert

**Subheadline:**
Our Phoenix shop features carefully curated succulents, cacti, and desert-adapted plants—plus pottery, planters, and everything you need to keep them thriving.

**CTA Button:** "Visit Our Shop"

---

### Intro Section

**Section Headline (H2):**
Handpicked for Arizona Living

**Body:**
Every plant in our shop is chosen because it can handle Phoenix's heat, sun, and low humidity. Whether you're looking for a statement piece for your living room or hardy outdoor plants for your garden, we've got options that won't just survive—they'll flourish.

No more guessing which plants will make it. Everything we carry comes with expert care advice tailored to our unique desert climate.

---

### Plant Categories Section

**Section Headline (H2):**
Browse by Category

**5 Category Cards (grid layout - 2 columns on tablet, 3 on desktop, stacked on mobile):**

---

**Category 1: Succulents & Cacti**

**Image:** Stock photo of assorted succulents in terracotta pots

**Headline (H3):** Succulents & Cacti

**Description:**
Low-maintenance, sculptural, and perfectly suited for Arizona. Our collection includes everything from tiny echeveria to dramatic agave and prickly pear. Ideal for both indoor and outdoor spaces.

**What You'll Find:**
- Agave varieties
- Aloe and echeveria
- Barrel and columnar cacti
- Sempervivum (hens and chicks)
- Jade plants

**Care Notes:**
Bright light, infrequent watering, well-draining soil. Perfect for Phoenix's dry climate.

---

**Category 2: Indoor Plants**

**Image:** Stock photo of snake plants and pothos in modern planters

**Headline (H3):** Indoor Plants

**Description:**
Bring greenery indoors with plants adapted to Arizona's low humidity and bright light. From snake plants to pothos, we stock varieties that tolerate the conditions inside Phoenix homes.

**What You'll Find:**
- Snake plants (Sansevieria)
- Pothos and philodendron
- ZZ plants
- Fiddle leaf fig (adapted varieties)
- Spider plants

**Care Notes:**
Bright indirect light, water when soil is dry. These plants handle dry indoor air beautifully.

---

**Category 3: Desert-Adapted Outdoor Plants**

**Image:** Stock photo of desert marigold and native plants

**Headline (H3):** Outdoor Plants

**Description:**
Transform your yard with plants built for the desert. Native and adapted species that require minimal water once established, handle full sun, and look stunning year-round.

**What You'll Find:**
- Desert marigold
- Red yucca
- Palo verde seedlings
- Texas sage
- Lantana

**Care Notes:**
Full sun, drought-tolerant once established. Perfect for xeriscaping and water-wise gardens.

---

**Category 4: Pottery & Planters**

**Image:** Stock photo of terracotta and ceramic planters

**Headline (H3):** Pottery & Planters

**Description:**
Complete your plant display with our selection of terracotta pots, ceramic planters, and decorative containers. Many feature drainage holes and come in sizes to fit any plant.

**What You'll Find:**
- Terracotta pots (classic and modern)
- Glazed ceramic planters
- Hanging planters
- Large statement pots for outdoor use
- Saucers and trays

---

**Category 5: Gardening Supplies**

**Image:** Stock photo of gardening tools and soil

**Headline (H3):** Gardening Supplies

**Description:**
Get everything you need to keep your plants thriving: cactus soil, fertilizers, watering tools, and more—all chosen for desert gardening.

**What You'll Find:**
- Cactus and succulent soil mix
- Fertilizers for desert plants
- Watering cans and misters
- Gardening gloves
- Pruning tools

---

### Why Shop With Us Section (Background: Warm Gray)

**Section Headline (H2):**
Why Buy Plants from Bloom & Basin?

**4 Points (2x2 grid):**

**Point 1:** Proven for Phoenix
We only stock plants that we know will thrive here. No guesswork, no disappointment—just plants suited to our climate.

**Point 2:** Expert Guidance
Not sure which plant is right for your space? Our team (led by shop manager Jake Thornton) knows every species we carry and can help you choose.

**Point 3:** Care Instructions Included
Every plant comes with Arizona-specific care tips. We want your plants to thrive, not just survive.

**Point 4:** Locally Owned
When you shop with us, you're supporting a local Phoenix business that's passionate about plants and sustainability.

---

### Visit Our Shop Section (White background)

**Section Headline (H2):**
Come See Us in Phoenix

**Body:**
Browse our full collection in person at our shop on 7th Street. Our team is here to answer questions, help you find the perfect plant, and share care tips.

**Contact Info (formatted nicely):**
📍 **Address:** 2847 N 7th Street, Phoenix, AZ 85014

🕐 **Hours:**
Monday - Friday: 9am - 6pm
Saturday: 9am - 5pm
Sunday: 10am - 4pm

**CTA Button:** "Get Directions"

---

### Final CTA Section

**Headline (H2):**
Visit Our Shop Today

**Body:**
Come explore our collection of desert-adapted plants, succulents, and pottery. Whether you're a seasoned plant parent or just getting started, we're here to help.

**CTA Buttons:**
- "Get Directions" (primary)
- "Call Us: (602) 555-0143" (secondary)

---

## PAGE 3: SERVICES (/services)

**Meta:**
- Title: "Landscaping Services Phoenix | Xeriscape Design & Installation"
- Description: "Professional landscape design, installation, and maintenance in Phoenix. Specializing in water-wise xeriscape, drought-tolerant plantings, and sustainable desert landscapes. Free quotes."

### Hero Section

**Headline (H1):**
Professional Landscaping for the Arizona Desert

**Subheadline:**
From custom xeriscape design to full installation and ongoing maintenance, we create stunning outdoor spaces that celebrate the desert and conserve water.

**CTA Button:** "Get a Free Quote"

---

### Intro Section

**Section Headline (H2):**
Landscapes Built for Arizona

**Body:**
Phoenix's climate demands a different approach to landscaping. Cookie-cutter solutions don't work here. That's why we specialize exclusively in desert-adapted landscapes—beautiful, sustainable outdoor spaces designed to thrive in heat, sun, and limited rainfall.

Whether you're starting from scratch or transforming an existing yard, our team brings deep expertise in xeriscape design, native plants, and water-wise irrigation. The result? A landscape you'll love that actually works with Arizona's environment, not against it.

---

### Services Section

**Section Headline (H2):**
Our Landscaping Services

**4 Service Offerings (cards layout, 2x2 grid on desktop, stacked on mobile):**

---

**Service 1: Landscape Design**

**Icon:** 📐 or design icon

**Headline (H3):** Custom Landscape Design

**Description:**
We create tailored landscape plans that balance beauty, sustainability, and your vision. Every design considers your property's sun exposure, soil conditions, water access, and how you want to use the space.

**What's Included:**
- On-site consultation and property assessment
- Custom design plan with plantings, hardscape, and irrigation
- Plant selection focused on drought-tolerant, desert-adapted species
- Material recommendations (gravel, pavers, decorative rock)
- 3D renderings or sketches (for larger projects)

**Perfect For:**
Homeowners planning a new landscape, HOA-compliant xeriscape conversions, commercial properties seeking sustainable outdoor spaces.

**CTA Button:** "Request a Design Consultation"

---

**Service 2: Landscape Installation**

**Icon:** 🛠️ or installation icon

**Headline (H3):** Landscape Installation

**Description:**
Our installation team brings your landscape design to life with expert craftsmanship and attention to detail. We handle everything from soil preparation and irrigation to planting and hardscaping.

**What's Included:**
- Complete site preparation
- Irrigation system installation (drip systems, timers, water-efficient zones)
- Planting of trees, shrubs, succulents, and groundcover
- Hardscape elements (pathways, patios, decorative rock)
- Mulch and soil amendments
- Final walkthrough and care instructions

**Perfect For:**
New construction homes, yard renovations and transformations, replacing grass lawns with xeriscape.

**CTA Button:** "Get an Installation Quote"

---

**Service 3: Landscape Maintenance**

**Icon:** ✂️ or maintenance icon

**Headline (H3):** Ongoing Landscape Maintenance

**Description:**
Keep your outdoor space looking its best year-round with our professional maintenance services. We handle pruning, seasonal plantings, irrigation management, and more—so you can enjoy your yard without the work.

**What's Included:**
- Seasonal pruning and trimming
- Irrigation system checks and adjustments
- Weed control
- Mulch and rock refresh
- Seasonal planting rotation (if desired)
- Fertilization for desert plants

**Perfect For:**
Busy homeowners, commercial properties, investment properties and rentals.

**CTA Button:** "Schedule Maintenance"

---

**Service 4: Xeriscape Consulting**

**Icon:** 💧 or consulting icon

**Headline (H3):** Xeriscape Consulting & Conversion

**Description:**
Ready to eliminate your grass lawn and embrace water-wise landscaping? Our xeriscape consulting service helps you transition to a beautiful, sustainable landscape that saves water, reduces maintenance, and looks better than traditional turf.

**What's Included:**
- Property assessment and water usage analysis
- Xeriscape design recommendations
- Plant palette for your specific conditions
- Irrigation efficiency planning
- Rebate and incentive guidance (Phoenix water conservation programs)

**Perfect For:**
Homeowners with high water bills, eco-conscious property owners, HOAs requiring drought-tolerant landscaping.

**CTA Button:** "Book a Xeriscape Consultation"

---

### Our Process Section (Background: Warm Gray)

**Section Headline (H2):**
How We Work

**4 Steps (horizontal timeline on desktop, vertical on mobile):**

**Step 1: Consultation**
We start with a free on-site visit to understand your vision, assess your property, and discuss options that fit your budget and timeline.

**Step 2: Design**
Our team creates a custom landscape plan tailored to your space. You'll review the design, make adjustments, and approve before we move forward.

**Step 3: Installation**
We bring your landscape to life with professional installation, quality materials, and attention to every detail.

**Step 4: Enjoy**
Your new landscape is ready! We provide care instructions and are available for ongoing maintenance if you'd like.

---

### Why Choose Us Section (White background)

**Section Headline (H2):**
Why Work with Us?

**4 Points (2x2 grid):**

**Desert Experts:** We specialize exclusively in desert landscapes. Our team knows which plants thrive, how to manage irrigation efficiently, and how to design for Arizona's unique conditions.

**Sustainable & Beautiful:** Water-wise doesn't mean boring. We create landscapes that are stunning, low-maintenance, and built to last in our climate.

**Local & Experienced:** Led by Maria Santos, who has 15 years of landscape design experience in Phoenix, our team understands the challenges and opportunities of desert landscaping.

**Full-Service:** From initial design through installation and maintenance, we handle it all. No need to coordinate multiple contractors—we've got you covered.

---

### Service Areas Section

**Section Headline (H2):**
Serving the Phoenix Metro Area

**Body:**
We proudly serve residential and commercial clients throughout the Phoenix metro area, including:

Phoenix | Scottsdale | Tempe | Mesa | Chandler | Gilbert | Glendale | Peoria

**CTA:** Not sure if we serve your area? Contact us.

---

### Testimonials Section (Background: Sand Cream)

**Section Headline (H2):**
What Our Clients Say

**2 Testimonials (side by side on desktop, stacked on mobile):**

**Testimonial 1:**
"Bloom & Basin transformed our backyard into an oasis. We get compliments from neighbors every week!"
— Sarah M., Scottsdale

**Testimonial 2:**
"Professional, creative, and they really listened to what we wanted. Our xeriscape is stunning."
— The Rodriguez Family, Phoenix

---

### Final CTA Section (Background: Sage Green, white text)

**Headline (H2):**
Ready to Transform Your Outdoor Space?

**Body:**
Whether you're looking for a complete landscape redesign or ongoing maintenance, we'd love to help. Contact us today for a free consultation and let's discuss how we can bring your vision to life.

**CTA Buttons (centered):**
- "Get a Free Quote" (white button)
- "Call Us: (602) 555-0143" (outlined white button)
- "Email: hello@bloomandbasin.com" (text link)

---

## PAGE 4: ABOUT (/about)

**Meta:**
- Title: "About Us | Bloom & Basin - Phoenix Plant Shop & Landscaping"
- Description: "Meet the team behind Bloom & Basin. Founded by landscape designer Maria Santos, we're Phoenix locals passionate about desert plants, sustainable landscaping, and helping you create beautiful spaces."

### Hero Section

**Headline (H1):**
Locally Rooted in Phoenix, Passionate About Plants

**Subheadline:**
We're more than a plant shop and landscaping company—we're desert gardening enthusiasts on a mission to help Phoenix embrace water-wise, beautiful outdoor spaces.

---

### Our Story Section

**Section Headline (H2):**
How Bloom & Basin Began

**Paragraph 1:**
Bloom & Basin was born from a simple belief: desert landscapes can be absolutely stunning when you work with nature, not against it. Founder Maria Santos grew up learning to garden from her grandmother in a small Phoenix yard filled with native plants and succulents. That early love of desert flora turned into a career, and after 15 years designing landscapes across the Phoenix metro, Maria wanted to create something different—a place that combined retail plant sales with expert landscape services, all centered around drought-tolerant, desert-adapted greenery.

**Paragraph 2:**
In 2022, Bloom & Basin opened its doors on 7th Street. The shop quickly became a go-to destination for plant lovers seeking species that actually thrive in Phoenix's heat and low rainfall. At the same time, our landscaping division grew as homeowners and businesses sought sustainable, beautiful outdoor spaces that conserve water and celebrate Arizona's natural environment.

**Paragraph 3:**
Today, we serve the Phoenix metro area with both retail plant sales and full-service landscaping. Whether you're shopping for a single succulent or planning a complete xeriscape transformation, our team brings the same passion, expertise, and commitment to helping you create spaces that flourish in the desert.

---

### Our Values Section (Background: Warm Gray)

**Section Headline (H2):**
What Drives Us

**4 Values (2x2 grid, icon + title + description):**

**Value 1:**
**Icon:** 🌵
**Title:** Desert Expertise
**Description:** We specialize exclusively in plants and landscapes suited to Arizona's climate. Every recommendation we make is backed by real experience and knowledge of what works in the heat, sun, and low rainfall of the Southwest.

**Value 2:**
**Icon:** 💧
**Title:** Sustainability First
**Description:** Water is precious in the desert. We're committed to promoting water-wise gardening, drought-tolerant plants, and landscapes that are beautiful without being wasteful.

**Value 3:**
**Icon:** ❤️
**Title:** Personalized Service
**Description:** We're a local, family-owned business, not a corporate chain. When you work with us, you get personalized attention from people who genuinely care about your success with plants.

**Value 4:**
**Icon:** 📚
**Title:** Education & Empowerment
**Description:** We don't just sell plants or install landscapes—we educate. Our goal is to empower you with the knowledge and confidence to maintain and enjoy your greenery for years to come.

---

### Meet the Team Section (White background)

**Section Headline (H2):**
The People Behind Bloom & Basin

**2 Team Member Cards (side by side on desktop, stacked on mobile):**

---

**Team Member 1:**

**Photo:** Professional headshot placeholder or stock photo of a woman in her 30s-40s outdoors

**Name:** Maria Santos
**Role:** Founder & Lead Landscape Designer

**Bio:**
Maria has been designing landscapes in Phoenix for over 15 years. She started learning to garden from her grandmother as a child and turned that passion into a career focused on sustainable, desert-adapted outdoor spaces. With a background in landscape architecture and a deep love for native plants, Maria leads the design and installation side of Bloom & Basin. When she's not designing landscapes, you'll find her hunting for rare succulents or advocating for water conservation in Arizona.

---

**Team Member 2:**

**Photo:** Professional headshot placeholder or stock photo of a man in his 20s-30s in a plant shop

**Name:** Jake Thornton
**Role:** Shop Manager

**Bio:**
Jake manages the retail side of Bloom & Basin and knows every single species in the shop. A self-proclaimed plant nerd, he can identify plants on sight and rattle off care instructions from memory. Before joining Bloom & Basin, Jake worked at botanical gardens and nurseries across the Southwest. He's passionate about helping customers find the perfect plants for their homes and answering the inevitable question: "Why does my succulent keep dying?" (Spoiler: it's probably overwatering.)

---

### Our Approach Section (Background: Sand Cream)

**Section Headline (H2):**
How We're Different

**4 Points (simple list format):**

✓ **No Cookie-Cutter Solutions:** Every property is different, and so is every client. We take the time to understand your space, your goals, and your lifestyle before making recommendations.

✓ **We Only Recommend What Works:** If a plant or landscape feature won't thrive in Phoenix, we won't suggest it. We're honest about what works and what doesn't in our climate.

✓ **Quality Over Volume:** We'd rather do a few projects exceptionally well than rush through dozens. Our reputation is built on craftsmanship and attention to detail.

✓ **Long-Term Relationships:** We're not a one-and-done business. Many of our landscaping clients return for maintenance, and our retail customers know us by name. We value long-term relationships built on trust and expertise.

---

### Visit Us Section (White background)

**Section Headline (H2):**
Come See Us in Phoenix

**Body:**
Our shop is located on 7th Street in Phoenix. Stop by to browse our plant collection, ask questions, or chat about your landscaping ideas. We'd love to meet you.

**Contact Info (nicely formatted):**
📍 2847 N 7th Street, Phoenix, AZ 85014

📞 (602) 555-0143

📧 hello@bloomandbasin.com

🕐 **Hours:**
Monday - Friday: 9am - 6pm
Saturday: 9am - 5pm
Sunday: 10am - 4pm

---

### Final CTA Section (Background: Sage Green, white text)

**Headline (H2):**
Let's Work Together

**Body:**
Whether you're shopping for a single plant or planning a landscape project, we're here to help. Stop by our shop, give us a call, or request a consultation for landscaping services.

**CTA Buttons:**
- "Get a Free Landscaping Quote" (white button)
- "Visit Our Shop" (outlined white button)
- "Contact Us" (text link)

---

## PAGE 5: CONTACT (/contact)

**Meta:**
- Title: "Contact Bloom & Basin | Visit Our Phoenix Plant Shop"
- Description: "Get in touch with Bloom & Basin. Visit our Phoenix shop, request a landscaping quote, or call us at (602) 555-0143. We're here to help with all your desert plant and landscaping needs."

### Hero Section

**Headline (H1):**
Get in Touch

**Subheadline:**
Whether you have questions about plants, want to schedule a landscaping consultation, or just want to say hello—we'd love to hear from you.

---

### Contact Options Section

**Section Headline (H2):**
How to Reach Us

**3 Options (cards layout, 3 columns on desktop, stacked on mobile):**

**Option 1:**
**Icon:** 🏪
**Title:** Visit Our Shop
**Description:** Stop by our Phoenix location to browse plants, ask questions, and get personalized recommendations from our team.

**Option 2:**
**Icon:** 📝
**Title:** Request a Quote
**Description:** Planning a landscaping project? Fill out the form below or give us a call to schedule a free on-site consultation.

**Option 3:**
**Icon:** 📞
**Title:** Call or Email
**Description:** Have a quick question? Reach out by phone or email and we'll get back to you promptly.

---

### Contact Information Section (Background: Warm Gray, large text)

**Layout:** Centered, prominent display

📍 **Address:**
2847 N 7th Street
Phoenix, AZ 85014

📞 **Phone:**
(602) 555-0143

📧 **Email:**
hello@bloomandbasin.com

🕐 **Shop Hours:**
Monday - Friday: 9am - 6pm
Saturday: 9am - 5pm
Sunday: 10am - 4pm

---

### Contact Form Section (White background)

**Form Headline (H2):**
Send Us a Message

**Form Instructions:**
Fill out the form below and we'll get back to you within 24 hours. For landscaping consultations, let us know your project scope and preferred contact method.

**Form Fields:**

1. **Name** (text input, required)
   - Placeholder: "Your full name"

2. **Email** (email input, required)
   - Placeholder: "your@email.com"

3. **Phone** (tel input, optional)
   - Placeholder: "(602) 555-0000"

4. **I'm interested in:** (dropdown or radio buttons, required)
   - Options:
     - Landscaping services (design, installation, maintenance)
     - Plant shop / retail questions
     - General inquiry
     - Other

5. **Message** (textarea, required)
   - Placeholder: "Tell us about your project or question..."
   - Rows: 5-6

**Submit Button:** "Send Message" (Sage green, full width or centered)

**Note:** Use a simple form service like Formspree or Vercel Forms for submission. Success message: "Thanks for reaching out! We'll get back to you within 24 hours."

---

### Map Section (Full-width)

**Section Headline (H2):**
Find Us in Phoenix

**Body:**
We're located on 7th Street in central Phoenix, just north of downtown. Plenty of parking available.

**Map Embed:**
Embed Google Maps for: 2847 N 7th Street, Phoenix, AZ 85014
(Use iframe or Google Maps embed)

**Directions Note:**
Easily accessible from I-10 and SR 51. Look for our sage green sign!

---

### Quick FAQ Section (Background: Sand Cream)

**Section Headline (H2):**
Quick Answers

**4 FAQs (accordion or simple list):**

**Q: Do you offer free landscaping consultations?**
A: Yes! We offer free on-site consultations for landscaping projects. Contact us to schedule.

**Q: Can I visit the shop without an appointment?**
A: Absolutely. No appointment needed—just stop by during business hours.

**Q: Do you deliver plants?**
A: For landscaping projects, yes. For retail purchases, delivery is available for large orders. Contact us for details.

**Q: What areas do you serve for landscaping?**
A: We serve the entire Phoenix metro area, including Scottsdale, Tempe, Mesa, Chandler, Gilbert, and surrounding communities.

---

### Social Media Section (White background)

**Section Headline (H2):**
Follow Us

**Body:**
Stay inspired with desert gardening tips, new plant arrivals, and project highlights. Follow us on social media!

**Social Links (with icons):**
- Instagram: @bloomandbasin
- Facebook: /bloomandbasinphx

---

### Final CTA Section (Background: Sage Green, white text)

**Headline (H2):**
We're Here to Help

**Body:**
Whether you're shopping for plants or planning a landscape transformation, our team is ready to assist. Stop by, call, or send us a message—we look forward to connecting with you.

**CTA Buttons:**
- "Call Us: (602) 555-0143" (white button)
- "Get Directions" (outlined white button)

---

## Technical Requirements

**Framework:** React with Tailwind CSS (Lovable.dev default)

**Responsive Design:**
- Mobile-first approach
- Test at: 375px (mobile), 768px (tablet), 1280px (desktop)
- Hamburger menu on mobile, full nav on desktop

**Accessibility:**
- All images have alt text
- Proper heading hierarchy (H1 → H2 → H3)
- WCAG AA color contrast compliance
- Keyboard navigable
- Form labels properly associated

**Performance:**
- Optimize images (compress, use appropriate sizes)
- Lazy load images below the fold
- Minimal dependencies

**Additional Features:**
- Sticky header that appears on scroll
- Smooth scroll to sections (if using anchor links)
- Hover states on buttons and cards
- Form validation
- Mobile-friendly navigation

---

## Stock Images / Placeholder Guidance

Use high-quality stock photos for:
- Desert landscapes with succulents and native plants
- Phoenix-area xeriscape gardens
- Indoor plant displays (succulents, snake plants, pothos)
- Terracotta pots and planters
- Gardening supplies
- Professional landscaping work in progress
- Team photos (use diverse, authentic-looking stock photos)

**Image Style:** Natural light, warm tones, earthy aesthetic, professional but approachable

---

## Final Notes

**Business Details:**
- Business Name: Bloom & Basin
- Tagline: "Desert-inspired greenery for your home and yard"
- Location: Phoenix, Arizona
- Address: 2847 N 7th Street, Phoenix, AZ 85014
- Phone: (602) 555-0143
- Email: hello@bloomandbasin.com
- Social: @bloomandbasin (Instagram), /bloomandbasinphx (Facebook)

**Brand Personality:**
- Friendly and knowledgeable
- Passionate about plants
- Approachable expert (not preachy)
- Warm Southwest personality
- Professional yet conversational

**Primary Goals:**
1. Generate landscaping consultation requests (primary conversion)
2. Drive foot traffic to retail shop
3. Educate visitors about desert-adapted plants
4. Build trust as local Phoenix experts

---

**Build all 5 pages with this exact content, brand styling, and structure. Make it beautiful, modern, responsive, and professional. Focus on clean design, excellent typography, and strategic use of the Sage Green and Terracotta colors throughout.**
