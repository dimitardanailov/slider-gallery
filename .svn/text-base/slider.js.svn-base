/*
 * jQuery Slider Gallery 
 * 
 * Copyright (c) Dimitar Danailov
 * Licensed under the MIT License:
 *   http://www.opensource.org/licenses/mit-license.php
 */

function Slider (container)
{
    this.container = container; //ul
    this.listItems = container.find('li'); // all list
    this.itemWidth = this.listItems.eq(0).width(); // width
    this.listItemsLength = this.listItems.length;
    
    this.currentListItem = 0;
    this.playAnimation = true;
    this.defaultPosition = 0;
    this.dotsContainer = null;
    this.dots = null;
    this.parentNode = container.parent();
    this.dotsPage = this.currentListItem;
    this.buttonIsActive = true;
}

/*** Hover ***/
Slider.prototype.hoverIn = function () 
{
    this.playAnimation = false;
};

Slider.prototype.hoverOut = function ()
{
    this.playAnimation = true;
};
/*** Hover ***/

Slider.prototype.cloneFirstItem = function ()
{
    var firstItem = this.listItems.eq(0).clone();   
    this.container.append(firstItem);
    this.defaultPosition = this.listItemsLength;
};

Slider.prototype.createDots = function ()
{
    var dotStandartClass = 'dot _silider_box-corners',
        dotClass = '', 
        dotsHtml = '';
    
    this.dotsContainer = this.parentNode.find('._slider_dots');

    this.listItems.each(function(i)
    {
        if (i > 0)
        {
            dotClass = dotStandartClass;
            
        }
        else
        {
            dotClass = dotStandartClass + ' dot-active';
        }
        
        dotsHtml += '<span class="' + dotClass + '" data-dot="'+  i + '"></span>';
    });
    
    this.dotsContainer.html(dotsHtml).show();
    this.dots = this.dotsContainer.find('.dot');
};

Slider.prototype.dotsTransition = function (dot)
{
    this.playAnimation = false;
    var activePage = dot.data('dot');
    
    this.changeActiveDot(activePage);
    this.resetPosition();
    this.currentListItem = activePage;
    this.transition();
};

Slider.prototype.setCurrentDirection = function (direction)
{
    this.playAnimation = false;
    
    if (this.buttonIsActive) 
    {    
        if (direction === 'next')
        {
            this.setCurrent();
        } 
        else
        {
            this.previousItem();
        }
    }
    
    this.transition();
};

Slider.prototype.animation = function ()
{
    if (this.playAnimation && this.parentNode.is(':visible'))
    {
        this.setCurrent();
        this.transition();
    }    
};

Slider.prototype.transition = function ()
{
    this.container.animate({'margin-left': -(this.currentListItem * this.itemWidth)});
};

Slider.prototype.setCurrent = function ()
{
    this.resetPosition();
    
    var position = this.currentListItem;
    
    position++;
    
    if (position < this.listItemsLength)
    {
        this.currentListItem++;
        this.dotsPage = this.currentListItem;
    }    
    else
    {
        this.currentListItem = this.defaultPosition;
        this.dotsPage = 0;
    }
    
    if (this.dots)
    {
        this.changeActiveDot(this.dotsPage);
    }    
};

Slider.prototype.changeActiveDot = function (activeIndex)
{
    this.dots.removeClass('dot-active');
    this.dots.eq(activeIndex).addClass('dot-active');
};

Slider.prototype.resetPosition = function ()
{
    if (this.currentListItem === this.listItemsLength)
    {
        this.container.css({'margin-left' : 0});
        this.currentListItem = 0;
    }
};

Slider.prototype.previousItem = function ()
{
    if (this.currentListItem > 0) 
    {    
        this.currentListItem  = this.currentListItem - 1;
        this.resetPosition();
        if (this.dots !== null)
        {
            this.changeActiveDot(this.currentListItem);
        }
    }
};