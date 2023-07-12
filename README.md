[https://apify.com/epctex/trulia-scraper](https://apify.com/epctex/trulia-scraper?fpr=yhdrb)

# Actor - Trulia Scraper

## Trulia scraper

Trulia is an online company dedicated to real estate. Through their user-friendly website, individuals can seamlessly explore and purchase new homes or find rental options that suit their needs. Furthermore, Trulia offers a platform for users to list and sell their current homes. As users contemplate their next move, they can access comprehensive data on local neighborhoods and area demographics, helping them make informed decisions.

The real estate market is always active. Individuals constantly seek resources to assist them in finding their ideal homes as they relocate. When developers embark on creating applications and websites focused on facilitating home purchases, sales, or rentals, they often turn to the Trulia API for valuable information.

Since Trulia doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Trulia data scraper supports the following features:

-   Property Details - You can retrieve all the information of a property

-   Home details - You can retrieve all the information about a home

-   Building details - You can retrieve all the information about a building

-   Sold properties, rental properties, sale properties - You can search by using sold, rental, and sale properties.

-   All filter options - You can filter through all available filtering options

## Bugs, fixes, updates, and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/trulia-scraper/issues).


## Input Parameters

The input of this scraper should be JSON containing the list of pages on Trulia that should be visited. Required fields are:

- `search`: (Optional) (String) The keyword that you can search on Trulia.

- `maxItems`: (Optional) (Array) Maximum number of listing items that you want as output. Default is all.

- `endPage`: (Optional) (Number) The page number that you want to end with. By default, there is no end page. This applies to all search requests and `startUrls` individually.

- `startUrls`: (Optional) (Array) URLs to start with. It should be a list or detailed URL.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as an argument and returns data that will be merged with the default output.

- `customMapFunction`: (Optional) (String) Function that takes each of the objects as an argument and returns data that will be mapped by the function itself.

- `proxy`: (Required) (Proxy Object) Select proxies to be used by your crawler.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that is explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor is optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detailed requests. If the actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.02-0.04 compute units.

### Trulia Scraper Input example

```json
{
  "startUrls": [
    "https://www.trulia.com/p/ny/bronx/895-tiffany-st-bronx-ny-10459--2008893028",
    "https://www.trulia.com/home/364-Ovington-Ave-Brooklyn-NY-11209-112508280",
    "https://www.trulia.com/building/the-tides-at-arverne-by-the-sea-190-beach-69th-st-arverne-ny-11692-2355011519",
    "https://www.trulia.com/sold/New_York,NY/",
    "https://www.trulia.com/for_rent/New_York,NY/",
    "https://www.trulia.com/for_sale/New_York,NY/p_oh/",
    "https://www.trulia.com/for_sale/New_York,NY/2p_beds/50000p_price/APARTMENT,CONDO,COOP,SINGLE-FAMILY_HOME_type/fsbo_lt/"
  ],
  "proxy": {
    "useApifyProxy": true
  },
  "endPage": 5,
  "maxItems": 100
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with a failure state and output an explanation of what is wrong.

## Trulia Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any language (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Trulia actor.

## Scraped Trulia Properties

The structure of each item in Trulia looks like this:

### Item Detail

```json
{
    "type": "property",
    "url": "https://www.trulia.com/building/the-tides-at-arverne-by-the-sea-190-beach-69th-st-arverne-ny-11692-2355011519",
    "title": "The Tides At Arverne By The Sea",
    "bathrooms": 1,
    "bedrooms": 2,
    "breadcrumbs": [
        "For Rent",
        "NY",
        "Arverne",
        "11692",
        "190 Beach 69th St"
    ],
    "description": "A new architectural masterpiece now dazzles the shores of the Rockaways with the addition of THE TIDES at Arverne By The Sea. Spectacular beachfront, affordable & luxurious apartments, offering modern open living spaces and high-end finishes.\n\nAmenities will include a roof deck with pool and lounge, indoor and outdoor dining experiences, private parking available for a fee, bike storage and more.",
    "floorSpace": "455-906 sqft",
    "propertyStatus": "for rent",
    "latitude": 40.588964,
    "longitude": -73.797741,
    "propertyType": "apartment",
    "listingType": "rental",
    "zipCode": "11692",
    "neighborhood": null,
    "city": "Arverne",
    "state": "NY",
    "id": "9948671957-2355011519",
    "price": {
        "min": 2450,
        "max": 4200
    },
    "images": [
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/00ca20c0f040f67e66bfc6738275e5fa-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/c3b67f3ae7b9b5c6bc592e7486cdcb14-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/c2cd77b11abf78327d4042c8df677bc8-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/16f5a43534ec132b5ca1da9b02ea7f97-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/e9d0102686c4d22f1ac4d6d75fdce88c-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/2d4113a185c84dc26cfa1068af1f6540-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/fe1666812b05be4d41dcf01a8adb4be6-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/4c59b15134c0591e804ccb83eaab332c-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/58d3ae266a718b577323b6bfa7cbbf5d-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/c6e53ffd7c82fd2848c1d4b926dfebbf-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/83b60f44e6f1f6196ee90bfc743d58e2-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/c39a598c24b3554024138dc38bd7819a-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/cb830d2ad215619a3370322c6889e087-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/466a081325f51a7a44febd8a01c90d5a-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/20809833b97bc3edbe91c42fbb35f690-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/5ea091e9e48506962c317c5b7a479b1d-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/858061113f10d352b6492791aef6399a-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/7aab2b39ec33627a55442310791044c1-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/0f2b8c29a3000db9cd613c768ce8518c-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/a28a665f5b190ee3755b5f8e354d0775-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/252e3b911fb0428b9f59a234c933f51d-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/ef841eb74f74e9265dff85e268aaf3cf-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/7b8a380c61fc80c6a9f8beda25453e00-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/b0d09a6c0668f33b0d049a5b07e72b2d-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/aac1218229b97b072175cd942abc3f15-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/e5aa1829c370d6070317501443cbd588-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/0f2ff63343f487961d3b0eba4ff9beba-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/ce897f9a55c774fc5484eac80fceb892-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/992c85c0e337f6bb58d13f421d322da4-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/082885ae16f81cc5f75383d76a88571d-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/1b8730f05ae2b5e86ad5244c9381afcc-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/d7b97d48459e7844b9ac438c6b0c2dbf-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/a6f242047396b5fc327de73f12b831eb-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/6b1d1adcd010ac46642f909eb0de717a-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/63c7fc6ab43b88d0ae456fa995d27b69-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/206b0f9bf61886db32a310f326dde717-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/61bbab3f3b80505fdb8e469f45a2d068-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/0afecb236b1f78ae77e5096c7207ba7f-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/b4d1528cee7c9f7ec61e54c87cf04ce9-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/46ae8427911cf9aa7fc47fbc51f0e65d-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/80fad49d795bb114c71f3bf569bad5ee-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/890ac2858884107133851b1c7eac5591-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/155af11bb8c07f9572880754e0516610-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/350db6634066f693536fbbe50881ea67-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/fc0b8db84953ec731a6a9f85eb0b53ec-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/0d02c2e27f406da6a2f1924eb7afea7b-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/715c72a252029ad1efc102f61e008f68-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/f8d197b8c51a667f6c581ee480c7b491-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/d212fc252db5f474b5314b4f4ca6246e-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/5e4e033042d3dc69e1315e57907336e3-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/b7b6332d8c7c08147389487e0195cfa4-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/f06c04478979b5c09e99b0b88498c4d9-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/6bdc7ae09aec1a22e51c13f4c927d93a-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/8c1a457975ecfe1dc621bbdafe7efd15-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/62c095f3f442434980fa1f677bdd1068-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/c81fe92f5ac3df4c5a8f2f94959de57e-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/80fae341dfe8afd530e261efe817f7dc-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/c93df7536a406eb4365f40aa999d22cf-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/f366de9d964c8f7e3523302337f8ed98-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/80319a908ac766ba63618625b20547bf-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/f5f88baa3ae8465c1a7313a260ec1d78-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/5ff63745b6216bf04800e4649d2121e5-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/c3806cd7f7d8d8abf0ecbbc1e96dee59-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/4e0e4cf5652bba988206a42993fff5c0-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/c5659502f3238e092b4e63a125618388-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/4da9264130506b586958219c1bf0c7e8-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/ed1a0aa1effba27c725ea76e30120a26-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/3a20782b74b78e7e6b706f8c5d0a98ff-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/b6edd7932c592a4892c6687941670c71-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/c61a38e79d20b17f9a2c4c07eaf3ad13-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/a0766c756cbdb6d23b820c98ac63504d-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/9fcc240d29395ce081c5648d308528b3-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/ca5a2b5b3d600606e950abbef1a04fe6-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/f939350115d136f05df9cd0eb7260a90-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/adaa0f8fb8ea7369f1d2775d329e5c49-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/36e6df1c37cc6053b8b37edc2797398c-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/774f585daf9356f0859f06af063a24b5-f_b.jpg",
        "https://www.trulia.com/pictures/thumbs_5/zillowstatic/fp/fcca6bad026537eba3b30e797c1e6557-f_b.jpg"
    ],
    "features": [
        {
            "Pets": "Dogs & Cats",
            "category": "Home Highlights"
        },
        {
            "Parking": "Contact Manager",
            "category": "Home Highlights"
        },
        {
            "Outdoor": "Patio, Deck, Pool",
            "category": "Home Highlights"
        },
        {
            "A/C": "Cooling only",
            "category": "Home Highlights"
        },
        {
            "Utilities Included": "Contact Manager",
            "category": "Home Highlights"
        },
        {
            "Listed": "41 days ago",
            "category": "Home Highlights"
        },
        {
            "attribute": "Water",
            "category": "View"
        },
        {
            "attribute": "Storage",
            "category": "Interior Details"
        },
        {
            "attribute": "Dishwasher",
            "category": "Appliances & Utilities"
        },
        {
            "attribute": "Disposal",
            "category": "Appliances & Utilities"
        },
        {
            "attribute": "Dryer",
            "category": "Appliances & Utilities"
        },
        {
            "attribute": "Refrigerator",
            "category": "Appliances & Utilities"
        },
        {
            "attribute": "Washer",
            "category": "Appliances & Utilities"
        },
        {
            "attribute": "Air Conditioning",
            "category": "Heating & Cooling"
        },
        {
            "attribute": "Elevator",
            "category": "Levels, Entrance, & Accessibility"
        },
        {
            "Floors": "Vinyl",
            "category": "Levels, Entrance, & Accessibility"
        },
        {
            "Property Type": "Apartment",
            "category": "Property Type / Style"
        },
        {
            "Rent Includes": "Unknown",
            "category": "Rental"
        },
        {
            "attribute": "Cats, small dogs, large dogs allowed",
            "category": "Rental"
        },
        {
            "Internet/Satellite": "Cable, High Speed Internet",
            "category": "Other"
        },
        {
            "attribute": "Club House",
            "category": "Community rooms"
        },
        {
            "attribute": "Fitness Center",
            "category": "Community rooms"
        },
        {
            "attribute": "Game Room",
            "category": "Community rooms"
        },
        {
            "attribute": "Lounge",
            "category": "Community rooms"
        },
        {
            "attribute": "Controlled access",
            "category": "Security"
        },
        {
            "attribute": "Balcony",
            "category": "Exterior Home Features"
        },
        {
            "attribute": "Barbeque Area",
            "category": "Exterior Home Features"
        },
        {
            "attribute": "Deck",
            "category": "Exterior Home Features"
        },
        {
            "attribute": "Patio",
            "category": "Exterior Home Features"
        },
        {
            "Parking": "Unknown",
            "category": "Parking & Garage"
        },
        {
            "attribute": "Pool",
            "category": "Pool"
        },
        {
            "Special Features": "Off Street Parking",
            "category": "Special Features"
        }
    ],
    "floorPlans": [
        {
            "title": "Studio (1 Floorplan)",
            "name": "6E",
            "image": "https://www.trulia.com/images/icons/no_fp_icon_320.jpg",
            "bedrooms": 0,
            "bathrooms": 1,
            "price": 2450,
            "floorSpace": "455 sqft",
            "availability": "Ask for Availability",
            "units": []
        },
        {
            "title": "2 Bedrooms (1 Floorplan)",
            "name": "6C",
            "image": "https://www.trulia.com/images/icons/no_fp_icon_320.jpg",
            "bedrooms": 2,
            "bathrooms": 2,
            "price": 4200,
            "floorSpace": "906 sqft",
            "availability": "Ask for Availability",
            "units": []
        }
    ]
}
```

## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that are available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
