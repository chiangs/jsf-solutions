# Lesson 3

[Previous Lesson](../lesson2/solutions.md)

<!-- Solutions below only -->

## Question Number / Name

## 08. Changing Attributes / Exercise
```
<div class="clown-hat" data-color="red" data-num-stripes="3">A Clown hat</div>

    <script>
        // Set an attribute with Element.setAttribute 
        const getClown = document.querySelector(".clown-hat");
        getClown.setAttribute('data-awesomeness', true);

        // Get an attribute with Element.getAttribute
        const getAwesome = getClown.getAttribute('data-awesomeness');
        console.log(title = "data-awesomeness:", getAwesome);

        // Get an attribute with Element.dataset
        const getNumStripes = getClown.dataset.numStripes;
        console.log(title="data-num-stripes:", getNumStripes);

        // Set an attribute with Element.dataset
        getClown.dataset.hatSize="huge";

        // Remove attribute with Element.removeAttribute
        getClown.removeAttribute('data-awesomeness');
    </script>
```

<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson4/solutions.md)
