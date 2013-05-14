<?php
    require_once 'DirectoryTool.php';
    
    $directoryTool = new DirectoryTool('slider');
    $files = $directoryTool->listFiles();
    
?>

<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>Gallery</title>
        
        <link rel="stylesheet" href="slider.css" type="text/css" media="all"/>
        <link rel="stylesheet" href="style.css" type="text/css" media="all"/>
        
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"></script>
        <script src ="slider.js" type="text/javascript"></script>
        
    </head>
    <body>
        <!-- content -->
        <div class="main_wrapper">
            <div class="slider-gallery-wrapper-arrows">
                <span class="slider-arrow slider-arrow-center slider-arrow-prev" 
                      data-dir="prev"></span>
                
                <div class="slider-gallery-wrapper">
                    <div class="slider-image-wrapper">

                        <div class="presentation-gallery containerWithClear">

                            <ul>
                                <?php
                                    foreach ($files as $file) {
                                ?>
                                    <li>
                                        <img src="<?php echo $file;?>" />
                                    </li>
                                <?php
                                    }
                                ?>
                            </ul>
                            <div class="_slider_dots"></div>
                        </div>

                    </div>
                </div>
                
                <span class="slider-arrow slider-arrow-center slider-arrow-next" 
                      data-dir="next"></span>
            </div>
            
            
        </div>
        
        <script type="text/javascript">
            (function() {
                
                var gallery = $('.presentation-gallery');
                var container = gallery.css('overflow', 'hidden').children('ul');
                var slider = new Slider(container);

                slider.cloneFirstItem();
                slider.createDots();

                container.hover(
                function()
                {
                    slider.hoverIn();
                }, 
                function()
                {
                    slider.hoverOut();
                });

                window.setInterval(function(){slider.animation();}, 8000);
                
                $('.slider-arrow').on('click', function() {
                    slider.setCurrentDirection( $(this).data('dir') );
                });
                
                slider.dots.click(function(){
                    slider.dotsTransition($(this));
                });
            })();
        </script>
    </body>
</html>
