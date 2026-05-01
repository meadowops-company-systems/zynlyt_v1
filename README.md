Zynlyt
Eat light. Feel Zyn.
Zynlyt is a Gen Z healthy eating lifestyle app — a smart nutritional intelligence layer on top of Swiggy's MCP APIs that scores every food order against a user's personal health goal before they place it. Not after they eat. Before they order.

What Problem We Are Solving
When a Gen Z person opens Swiggy today, they see restaurant ratings, delivery time, and price. They see zero nutritional context. They spend 8 minutes on average deciding what to order — often opening Google separately to search for calories, then coming back to Swiggy to order anyway.
Zynlyt eliminates that entire journey. Every dish on Swiggy gets a Zyn Score — a 0 to 100 nutritional rating calculated against the user's personal goal — before the cart is built. The ordering decision that took 8 minutes now takes under 90 seconds.

What Zynlyt Does
Zynlyt adds a personalised nutritional intelligence layer on top of Swiggy's live food ordering API. It does not replace Swiggy. It enhances the ordering experience for health-conscious users, particularly Indian Gen Z aged 18 to 28.
When a user opens Zynlyt, they see Swiggy's restaurants reranked by Zyn Score match for their personal goal. Every dish shows calories, protein, carbohydrates, fat, and a one-line goal verdict. The user adds to cart, the best coupon is auto-applied, and the order is placed through Swiggy. Zynlyt never handles money. Swiggy processes every transaction.

Core User Goal Profiles
Users select one goal on onboarding. The Zyn Score algorithm weights nutritional factors differently per goal.
Build Muscle and Get Lean — weights protein at 40 percent, penalises refined carbs and empty calories.
Glow Skin and Feel Light — weights anti-inflammatory foods, penalises processed sugars and high-GI items.
Manage PCOD — weights hormone-friendly nutrients, flags inflammatory ingredients.
Diabetes and BP Safe — weights glycaemic index heavily, flags high-GI and high-sodium dishes.

Swiggy MCP APIs Used
This project integrates with three Swiggy MCP servers across the following tools:
Swiggy Food MCP Server
search_restaurants — fetches nearby restaurants by user location, used to build the Zyn-ranked home feed.
get_restaurant_menu — retrieves full menu for a selected restaurant, used to run Zyn Score calculation per dish.
search_menu — dish-level search within a restaurant, used for the search and filter experience.
your_go_to_items — fetches returning user's frequently ordered items, used for personalised quick-reorder suggestions.
fetch_food_coupons — fetches all available coupons for a restaurant, used for auto-coupon stacking on checkout.
apply_food_coupon — applies the best available coupon to the cart automatically.
update_food_cart — builds the cart as the user adds dishes.
get_food_cart — reads current cart state for the combined Zyn Score display.
place_food_order — places the confirmed order through Swiggy's infrastructure.
track_food_order — provides live order status inside Zynlyt after order placement.
get_food_orders — retrieves order history for the weekly Zyn Report generation.
Swiggy Instamart MCP Server (Version 2 — Month 6 onwards)
search_products — searches Instamart grocery catalogue for Zyn scoring of grocery orders.
update_cart — builds Instamart cart with Zyn-scored grocery items.
get_cart — reads Instamart cart for combined grocery Zyn Score.
checkout — passes Instamart cart to Swiggy checkout.
track_order — live tracking of Instamart orders.

Technical Architecture
Frontend: React Native — single codebase for iOS and Android. Dark mode default. Designed for sub-30-second onboarding from first open to first scored restaurant feed.
Backend: Node.js with Supabase for database, authentication, and real-time data. All user data stored with row-level security. No user data exported to third parties.
Authentication: Swiggy OAuth 2.1 for user account connection. Supabase Auth for Zynlyt account management.
Zyn Score Engine: Claude API (claude-sonnet-4-6) receives dish name, restaurant name, and cuisine type and returns structured nutritional estimates in JSON. Estimates are weighted against the user's active goal profile to produce the final Zyn Score. A hand-built seed database of 500 common Indian restaurant dishes provides consistent, low-latency scoring for frequently ordered items without repeated API calls.
Analytics: PostHog for product analytics. No third-party advertising SDKs.

Swiggy MCP Compliance
Zynlyt is designed from the ground up to comply fully with Swiggy's MCP terms and ground rules.
Swiggy attribution is mandatory. Every ordering screen, cart screen, checkout screen, and order tracking screen displays "Powered by Swiggy" clearly. Users always know their order is processed by Swiggy.
Prices, delivery times, and availability are displayed exactly as returned by Swiggy's APIs. Zynlyt never modifies or misrepresents Swiggy's commerce data.
The Zyn Score ranking algorithm is based purely on nutritional scoring against the user's goal profile. It is never influenced by restaurant payments or any commercial arrangement.
APIs are called only on real user-triggered actions. No background scraping, no batch catalogue harvesting, no automated loops through Swiggy's restaurant or menu data.
User health goal data is stored encrypted in Supabase with row-level security and is never shared with Swiggy or any third party.
Rate limits are respected. All traffic is real user-generated traffic only.

What We Are Building — Status
Zynlyt is currently in pre-build stage. This repository documents the complete product concept, planned API integration architecture, technical stack decisions, and compliance framework ahead of MCP access approval.
We are applying for Swiggy Builders Club MCP access as the first step in the build process. Code development begins immediately upon API key receipt.

Planned Build Timeline
Week 1 to 2: MCP access setup, Supabase schema design, Swiggy OAuth integration, seed database of 500 Indian restaurant dishes.
Week 3 to 4: React Native app — onboarding screen, home feed with Zyn-ranked restaurants, dish detail screen, cart and checkout flow, order tracking screen.
Week 5 to 6: Beta launch in Hyderabad to 100 users. Real orders. Real Zyn Scores. Iteration on feedback.
Week 7 to 8: Streak system, weekly Zyn Report shareable card, push notifications.
Month 3: 1,000 active users. First influencer partnership. Swiggy demo submission.

Brand
Name: Zynlyt
Tagline: Eat light. Feel Zyn.
Category: Gen Z healthy eating lifestyle app
Primary colour: Cyber Lime #C5F02A
Dark base: Midnight Bark #0C110B
Secondary: Digital Lavender #C4B5F5
Domain: zynlyt.in

Legal
This product is built on Swiggy's Builders Club MCP platform under the Swiggy MCP integration agreement. All Swiggy trademarks, brand assets, and data remain the property of Bundl Technologies Pvt Ltd. Zynlyt operates in full compliance with Swiggy's MCP terms, data protection requirements, and branding guidelines.
User health data is handled under Zynlyt's own privacy policy in compliance with India's Digital Personal Data Protection Act 2023.

Zynlyt — Built on Swiggy Builders Club MCP
