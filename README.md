# DynamicHoverWithJustClass_JS
Dynamic hover individual by hover with just a class Javascript Design for custom flip or hover box for any page wp builder! 

```HTML

<!-- TILE OR DIV TO BE HOVER -->
 <div id="container" class="v2-hover-app">

   <!-- CURRENT TO BE HIDE -->
   <div class="v2-hover-current"> CURRENT EXT AND ICON </div>
   <!-- / CURRENT TO BE HIDE -->
   <!-- ACTIVE TO BE SHOW -->
   <div class="v2-hover-active"> DESCRIPTION </div>
   <!-- / ACTIVE TO BE SHOW -->

 </div>
<!-- / TILE OR DIV TO BE HOVER -->

```

```JS

    // CLASS CURRENT DATA TO BE SHOW 
    const activeHover  = document.querySelectorAll('.v2-hover-active');
    // CLASS FOR DIV or TILE NEED TO BE HOVER | 
    const allTiles     = document.querySelectorAll('.v2-hover-app');
    
    // Hide this target each hover
    let hideThis = function( target ) {
        
        if( target ) {
     
            target.forEach(function( thisElem ) {
              thisElem.style.display = 'none';    
            });
            
        }
    }
    
    let showThis = function( target ) {
        
        if( target ) {
            
            target.forEach(function( thisElem ) {
                if(thisElem) {
                  thisElem.style.cursor  = 'pointer';     
                  thisElem.style.display = ''; 
                }
            });
            
        }
    }
    
    // Fetch children array element
    let fetchChildElem = function( sE ) {
        
        return sE.srcElement.childNodes;
        
    }
    
    // Get from array each click target
    let srcElementHide = function( sE ) {
        
        let childNodes = Array.from(fetchChildElem(sE));
        let v2HoverCurrent = 'v2-hover-current';
        let v2HoverActive  = 'v2-hover-active';
        
        let v2HoverCurrentData = childNodes.filter(node => 
          node.nodeType === 1 && node.classList.contains(v2HoverCurrent)
        );
        
        let v2HoverActiveData = childNodes.filter(node => 
          node.nodeType === 1 && node.classList.contains(v2HoverActive)
        );
        
        hideThis(v2HoverCurrentData);
        showThis(v2HoverActiveData);

    }
    
    let srcElementShow = function( sE ) {
        
        let childNodes = Array.from(fetchChildElem(sE));
        let v2HoverCurrent = 'v2-hover-current';
        let v2HoverActive  = 'v2-hover-active';
        
        let v2HoverCurrentData = childNodes.filter(node => 
          node.nodeType === 1 && node.classList.contains(v2HoverCurrent)
        );
        
        let v2HoverActiveData = childNodes.filter(node => 
          node.nodeType === 1 && node.classList.contains(v2HoverActive)
        );
        
        hideThis(v2HoverActiveData);
        showThis(v2HoverCurrentData);
        
    }
    
    let eventActiveHover = function(datas , event ) {
        
        const eventEnter = 'mouseenter';
        const eventOut   = 'mouseleave';
        
        if(event === eventEnter) {
            
           datas.forEach(function( thisClass ) {
            
              thisClass.addEventListener(event, function(  key, trget ) {
                srcElementHide(key);
              });    
            
            });
       
        } else if(event ===  eventOut) {
            
              datas.forEach(function( thisClass ) {
            
              thisClass.addEventListener(event, function(  key, trget ) {
                srcElementShow(key);
              });    
            
            });
            
        }
        
    }
    
    if(activeHover) {
      activeHover.forEach(function( thisClass ) {
       thisClass.style.display = 'none';
      });
    }
    
     if(allTiles) { 
      eventActiveHover(allTiles, 'mouseenter'); 
      eventActiveHover(allTiles, 'mouseleave'); 
     }


```
