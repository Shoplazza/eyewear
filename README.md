# Shoplazza Eyewear Merchant Onboarding Process for Tech Support Engineer and Solution Partners

- Store establishing 
  - This process is usually being done by AM, staying close with them in case they need any help.
- Items Import
  - Import from Shoplify: Using our built in import from Shopify feature or check with @Zidane Wu , their team has done this before and they have the script to migrate it. 
    - However, there are always expectations that may not work with the existing import script, for example: https://drlenschange.com/products/reading-1-50-index-td2-super-tough-anti-scratch this store created different product in shopify for one single type of lenses. In this case, you are required to design a custom flow with the merchant to help them build a store with smooth purchase experience.
  - Import from CSV/Excel that merchant provided: In the common cases, the merchants are able to export their products info as CSV/Excel from varity of sources. What you need to do is to format the CSV/Excel in the form of import tamplates get in our admin panel. 
[Image]
    - If the merchant provided multiple CSV/Excel becuase they are using different CMS/PMS to manage the product info, make sure there is a unique indentifier that can asscioated the same item cross the sheets
    - If the merchant only has offline image assets, you can upload it to S3 (you have to apply for one if you don't have it already) or follow How to make a mass amount of image assets accessible on the public internet to host it on your own computer
    - Also check with the merchant what info or parameters need to put in the description.
  - Import from an existing website that the merchant owns:
    - Ensure that the merchant owns the website, we don't want to get into any copyright issue with image assets and so. 
    - Starting with web crawling the links for the products, usually these links can be found in the sitemap if there is one. If there are no sitemaps, you might have to use a more manual way to fetch the links.
    - The majority of the website will have variants in a product page. Which means you might not be able to gather information by clicking the webpage to switch selected variant types. In order to webscriping data in these website, a headless browser is recomanded. Puppeteer is the one I used https://pptr.dev/ that can simulate the clicks
      - May ask the merchant to turn off bot detection if we get blocked.
    - The goal for this step is to generate a shoplazza importable product sheet or upload the product thru API.
- Theme customization
  - The theme customization will be based on the theme "Bright". When you start working on it, make sure you are working on the latest version.
  - You can followShoplazza Theme Development Starter Guide to start the theme development.
    - Comparing to tailwindcss, boostrap, natives css/scss is recomanded it can help to revent execesive DOM size, but I am open to switch in case we need to reduce the workload.
    - Try not to introduce complicated JS libaray as these usually affacts SEO.
  - Eyewear Theme Customization Starter Guide  is also a good resource for you to understand better with bussiness
  - Our design team will deliver a figma design to you like this and highlight which part needs customization: https://www.figma.com/file/Re70z0Bge7ll1tuBcTcx6l/MUJOSH-%E4%B8%BB%E9%A2%98%E5%AE%9A%E5%88%B6?type=design&node-id=29-1685&mode=design&t=z6NcvPu80TuzTbeX-0
  - Some merchants will require to have their product description or parameters in a nicer design like this:
[Image]
  - My recomandation is to generate the whole section in html at the time importing product excel sheet, that's a nice work around as our excel import doesn't support metafields, and it's usually exccessive amount of the of the work going thru the OpenAPI create metafields there and links the field to products.
