# Udemy_scrapper
a scrapper for Udemy designed by me using javascript which will run in browser's console  
Code snippet to print all the index : 
```var elements = document.querySelectorAll("span.section--section-title--svpHP");

if (elements.length > 0) {
    elements.forEach(function(element) {
        console.log(element.textContent.trim());
    });
} else {
    console.log("No elements found with the specified class name");
}
```


To print course title :  

``` var elements = document.querySelectorAll(".ud-heading-xl.clp-lead__title.clp-lead__title--small");

if (elements.length > 0) {
    elements.forEach(function(element) {
        console.log(element.textContent.trim());
    });
} else {
    console.log("No elements found with the specified class name");
}

```


To print Ratings: 
```
var elements = document.querySelectorAll(".clp-lead__badge-ratings-enrollment");

if (elements.length > 0) {
    elements.forEach(function(element, index) {
        if (index > 0) {
            console.log(" "); // Add space between elements
        }
        console.log(element.textContent.trim());
    });
} else {
    console.log("No elements found with the specified class name");
}
```


To print Price : 
```
var elements = document.querySelectorAll(".base-price-text-module--price-part---xQlz.ud-clp-discount-price.ud-heading-xl");

if (elements.length > 0) {
    elements.forEach(function(element, index) {
        console.log(element.textContent.trim());
    });
} else {
    console.log("No elements found with the specified class name");
}
```



To print content length : 
```
var elements = document.querySelectorAll(".curriculum--content-length--V3vIz");

if (elements.length > 0) {
    elements.forEach(function(element, index) {
        console.log(element.textContent.trim());
    });
} else {
    console.log("No elements found with the specified class name");
}

```

Only rating value : 
```
var elements = document.querySelectorAll(".clp-lead__badge-ratings-enrollment");

if (elements.length > 0) {
    elements.forEach(function(element, index) {
        var ratingText = element.textContent.trim();
        var rating = ratingText.split(" ")[1]; // Extracting the rating part
        if (index > 0) {
            console.log(" "); // Add space between elements
        }
        console.log(rating);
    });
} else {
    console.log("No elements found with the specified class name");
}
```












To print whole data in tabular and json format : 
```
// Selecting course titles
var courseTitles = document.querySelectorAll(".ud-heading-xl.clp-lead__title.clp-lead__title--small");
var courseTitlesArray = Array.from(courseTitles).map(function(element) {
    return {
        "Course Title": element.textContent.trim()
    };
});

// Selecting ratings
var ratings = document.querySelectorAll(".clp-lead__badge-ratings-enrollment");
var ratingsArray = Array.from(ratings).map(function(element) {
    return {
        "Ratings": element.textContent.trim()
    };
});

// Selecting prices
var prices = document.querySelectorAll(".base-price-text-module--price-part---xQlz.ud-clp-discount-price.ud-heading-xl");
var pricesArray = Array.from(prices).map(function(element) {
    return {
        "Price": element.textContent.trim()
    };
});

// Selecting content lengths
var contentLengths = document.querySelectorAll(".curriculum--content-length--V3vIz");
var contentLengthsArray = Array.from(contentLengths).map(function(element) {
    return {
        "Content Length": element.textContent.trim()
    };
});

// Combining all data into one array of objects
var resultsArray = [];
for (var i = 0; i < Math.max(courseTitlesArray.length, ratingsArray.length, pricesArray.length, contentLengthsArray.length); i++) {
    var result = {};
    if (courseTitlesArray[i]) {
        result["Course Title"] = courseTitlesArray[i]["Course Title"];
    }
    if (ratingsArray[i]) {
        result["Ratings"] = ratingsArray[i]["Ratings"];
    }
    if (pricesArray[i]) {
        result["Price"] = pricesArray[i]["Price"];
    }
    if (contentLengthsArray[i]) {
        result["Content Length"] = contentLengthsArray[i]["Content Length"];
    }
    resultsArray.push(result);
}

// Printing results in tabular format
console.table(resultsArray);

// Printing results in JSON format
console.log(JSON.stringify(resultsArray, null, 2));
```






ALL DETAILS IN ONE

``` // Selecting course titles
var courseTitles = document.querySelectorAll(".ud-heading-xl.clp-lead__title.clp-lead__title--small");
var courseTitlesArray = Array.from(courseTitles).map(function(element) {
    return {
        "Course Title": element.textContent.trim()
    };
});

// Selecting ratings
var ratings = document.querySelectorAll(".clp-lead__badge-ratings-enrollment");
var ratingsArray = Array.from(ratings).map(function(element) {
    return {
        "Ratings": element.textContent.trim()
    };
});

// Selecting prices
var prices = document.querySelectorAll(".base-price-text-module--price-part---xQlz.ud-clp-discount-price.ud-heading-xl");
var pricesArray = Array.from(prices).map(function(element) {
    return {
        "Price": element.textContent.trim()
    };
});

// Selecting content lengths
var contentLengths = document.querySelectorAll(".curriculum--content-length--V3vIz");
var contentLengthsArray = Array.from(contentLengths).map(function(element) {
    return {
        "Content Length": element.textContent.trim()
    };
});

// Extracting total rating
var totalRatingElements = document.querySelectorAll(".clp-lead__badge-ratings-enrollment");
var totalRatingsArray = [];
totalRatingElements.forEach(function(element, index) {
    var ratingText = element.textContent.trim();
    var rating = ratingText.split(" ")[1]; // Extracting the rating part
    totalRatingsArray.push({ "Total Rating": rating });
});

// Combining all data into one array of objects
var resultsArray = [];
for (var i = 0; i < Math.max(courseTitlesArray.length, ratingsArray.length, pricesArray.length, contentLengthsArray.length, totalRatingsArray.length); i++) {
    var result = {};
    if (courseTitlesArray[i]) {
        result["Course Title"] = courseTitlesArray[i]["Course Title"];
    }
    if (ratingsArray[i]) {
        result["Ratings"] = ratingsArray[i]["Ratings"];
    }
    if (pricesArray[i]) {
        result["Price"] = pricesArray[i]["Price"];
    }
    if (contentLengthsArray[i]) {
        result["Content Length"] = contentLengthsArray[i]["Content Length"];
    }
    if (totalRatingsArray[i]) {
        result["Total Rating"] = totalRatingsArray[i]["Total Rating"];
    }
    resultsArray.push(result);
}

// Printing results in tabular format
console.table(resultsArray);

// Printing results in JSON format
console.log(JSON.stringify(resultsArray, null, 2));
```








SEARCH COURSE : 

```
var links = document.querySelectorAll("a");

// Loop through each <a> element
links.forEach(function(link) {
    // Check if the element has an href attribute
    if (link.hasAttribute("href")) {
        // Get the href value
        var href = link.getAttribute("href");
        // Get the text content of the <a> element
        var textContent = link.textContent.trim();
        // Check if the text content contains the keyword
        var keyword = "Python"; // Replace with your keyword
        if (textContent.toLowerCase().includes(keyword.toLowerCase())) {
            // Print the data for elements containing href attribute and keyword
            console.log(link.outerHTML);
        }
    }
});
```




To search and print datas in tabular format : 
```

// Initialize arrays to store data
var courseTitlesArray = [];
var ratingsArray = [];
var numberOfReviewsArray = [];
var timeArray = [];
var numberOfLecturesArray = [];
var instructionalLevelArray = [];
var currentPriceArray = [];
var originalPriceArray = [];

// Select all <a> elements on the page
var links = document.querySelectorAll("a");

// Loop through each <a> element
links.forEach(function(link) {
    // Check if the element has an href attribute
    if (link.hasAttribute("href")) {
        // Get the href value
        var href = link.getAttribute("href");
        // Check if the data-testid attributes are present
        var seoHeadline = link.querySelector('[data-testid="seo-headline"]');
        var seoRating = link.querySelector('[data-testid="seo-rating"]');
        var seoNumReviews = link.querySelector('[data-testid="seo-num-reviews"]');
        var seoContentInfo = link.querySelector('[data-testid="seo-content-info"]');
        var seoNumLectures = link.querySelector('[data-testid="seo-num-lectures"]');
        var seoInstructionalLevel = link.querySelector('[data-testid="seo-instructional-level"]');
        var seoCurrentPrice = link.querySelector('[data-testid="seo-current-price"]');
        var seoOriginalPrice = link.querySelector('[data-testid="seo-original-price"]');
        
        // Check if all data-testid attributes are present
        if (seoHeadline && seoRating && seoNumReviews && seoContentInfo && seoNumLectures && seoInstructionalLevel && seoCurrentPrice && seoOriginalPrice) {
            // Extract text content from data-testid attributes
            var title = seoHeadline.textContent.trim();
            var ratings = seoRating.textContent.trim();
            var numberOfReviews = seoNumReviews.textContent.trim();
            var time = seoContentInfo.textContent.trim();
            var numberOfLectures = seoNumLectures.textContent.trim();
            var instructionalLevel = seoInstructionalLevel.textContent.trim();
            var currentPrice = seoCurrentPrice.textContent.trim();
            var originalPrice = seoOriginalPrice.textContent.trim();
            
            // Push data into respective arrays
            courseTitlesArray.push({ "Course Title": title });
            ratingsArray.push({ "Ratings": ratings });
            numberOfReviewsArray.push({ "Number of Reviews": numberOfReviews });
            timeArray.push({ "Time": time });
            numberOfLecturesArray.push({ "Number of Lectures": numberOfLectures });
            instructionalLevelArray.push({ "Instructional Level": instructionalLevel });
            currentPriceArray.push({ "Current Price": currentPrice });
            originalPriceArray.push({ "Original Price": originalPrice });
        }
    }
});

// Combine data into one array of objects
var resultsArray = [];
for (var i = 0; i < courseTitlesArray.length; i++) {
    var result = {
        "Course Title": courseTitlesArray[i]["Course Title"],
        "Ratings": ratingsArray[i]["Ratings"],
        "Number of Reviews": numberOfReviewsArray[i]["Number of Reviews"],
        "Time": timeArray[i]["Time"],
        "Number of Lectures": numberOfLecturesArray[i]["Number of Lectures"],
        "Instructional Level": instructionalLevelArray[i]["Instructional Level"],
        "Current Price": currentPriceArray[i]["Current Price"],
        "Original Price": originalPriceArray[i]["Original Price"]
    };
    resultsArray.push(result);
}

// Printing results in tabular format
console.table(resultsArray);

// Printing results in JSON format
console.log(JSON.stringify(resultsArray, null, 2));

```











To search and find the best rated in descending order and print it : 

```// Initialize arrays to store data
var courseTitlesArray = [];
var ratingsArray = [];
var numberOfReviewsArray = [];
var timeArray = [];
var numberOfLecturesArray = [];
var instructionalLevelArray = [];
var currentPriceArray = [];
var originalPriceArray = [];

// Select all <a> elements on the page
var links = document.querySelectorAll("a");

// Loop through each <a> element
links.forEach(function(link) {
    // Check if the element has an href attribute
    if (link.hasAttribute("href")) {
        // Get the href value
        var href = link.getAttribute("href");
        // Check if the data-testid attributes are present
        var seoHeadline = link.querySelector('[data-testid="seo-headline"]');
        var seoRating = link.querySelector('[data-testid="seo-rating"]');
        var seoNumReviews = link.querySelector('[data-testid="seo-num-reviews"]');
        var seoContentInfo = link.querySelector('[data-testid="seo-content-info"]');
        var seoNumLectures = link.querySelector('[data-testid="seo-num-lectures"]');
        var seoInstructionalLevel = link.querySelector('[data-testid="seo-instructional-level"]');
        var seoCurrentPrice = link.querySelector('[data-testid="seo-current-price"]');
        var seoOriginalPrice = link.querySelector('[data-testid="seo-original-price"]');
        
        // Check if all data-testid attributes are present
        if (seoHeadline && seoRating && seoNumReviews && seoContentInfo && seoNumLectures && seoInstructionalLevel && seoCurrentPrice && seoOriginalPrice) {
            // Extract text content from data-testid attributes
            var title = seoHeadline.textContent.trim();
            var ratings = parseFloat(seoRating.textContent.trim().split(" ")[1]); // Extract only the numeric rating
            var numberOfReviews = parseInt(seoNumReviews.textContent.trim().split(" ")[0]); // Extract only the numeric number of reviews
            var time = seoContentInfo.textContent.trim();
            var numberOfLectures = parseInt(seoNumLectures.textContent.trim().split(" ")[0]); // Extract only the numeric number of lectures
            var instructionalLevel = seoInstructionalLevel.textContent.trim();
            var currentPrice = seoCurrentPrice.textContent.trim();
            var originalPrice = seoOriginalPrice.textContent.trim();
            
            // Push data into respective arrays
            courseTitlesArray.push({ "Title": title });
            ratingsArray.push({ "Rating": ratings });
            numberOfReviewsArray.push({ "Reviews": numberOfReviews });
            timeArray.push({ "Time": time });
            numberOfLecturesArray.push({ "Lectures": numberOfLectures });
            instructionalLevelArray.push({ "Level": instructionalLevel });
            currentPriceArray.push({ "Current": currentPrice });
            originalPriceArray.push({ "Original": originalPrice });
        }
    }
});

// Combine data into one array of objects
var resultsArray = [];
for (var i = 0; i < courseTitlesArray.length; i++) {
    var result = {
        "Title": courseTitlesArray[i]["Title"],
        "Rating": ratingsArray[i]["Rating"],
        "Reviews": numberOfReviewsArray[i]["Reviews"],
        "Time": timeArray[i]["Time"],
        "Lectures": numberOfLecturesArray[i]["Lectures"],
        "Level": instructionalLevelArray[i]["Level"],
        "Current": currentPriceArray[i]["Current"],
        "Original": originalPriceArray[i]["Original"]
    };
    resultsArray.push(result);
}

// Sort resultsArray based on Rating in descending order
resultsArray.sort(function(a, b) {
    return b.Rating - a.Rating;
});

// Printing results in tabular format
console.table(resultsArray);

// Printing results in JSON format
console.log(JSON.stringify(resultsArray, null, 2));

```




TO DOWNLOAD THE DATA IN CSV FILE 


```// Convert resultsArray to CSV format
var csvContent = "Course Title,Ratings,Number of Reviews,Time,Number of Lectures,Instructional Level,Current Price,Original Price\n";
resultsArray.forEach(function(row) {
    // Check if Current Price and Original Price fields exist
    if (row["Current Price"]) {
        // Replace rupee symbol with "Rs"
        row["Current Price"] = row["Current Price"].replace("₹", "Rs ");
    }
    if (row["Original Price"]) {
        // Replace rupee symbol with "Rs"
        row["Original Price"] = row["Original Price"].replace("₹", "Rs ");
    }

    // Convert row object to CSV row
    var csvRow = Object.values(row).map(value => `"${value}"`).join(",");
    csvContent += csvRow + "\n";
});

// Create a Blob containing the CSV data
var blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });

// Create a download link
var link = document.createElement("a");
if (link.download !== undefined) { // Check if download attribute is supported
    var url = URL.createObjectURL(blob);
    link.setAttribute("href", url);
    link.setAttribute("download", "course_data.csv");
    document.body.appendChild(link);
    link.click(); // Click the link to trigger the download
    document.body.removeChild(link); // Clean up
} else {
    console.log("Your browser does not support the download attribute.");
}
```
