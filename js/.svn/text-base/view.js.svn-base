'use strict';

var globalTView;
var icvCount =0;
/**
 * A function that creates and returns all of the model classes and constants.
  */
function createViewModule() {

    var LIST_VIEW = 'LIST_VIEW';
    var GRID_VIEW = 'GRID_VIEW';
    var RATING_CHANGE = 'RATING_CHANGE';

    /**
     * An object representing a DOM element that will render the given ImageModel object.
     */
    var ImageRenderer = function(imageModel) {
        this.imageModel=imageModel;
        this.curView=LIST_VIEW;
        this.starListener =0;
        this.setImageModel(imageModel);
    };

    _.extend(ImageRenderer.prototype, {

        /**
         * Returns an element representing the ImageModel, which can be attached to the DOM
         * to display the ImageModel.
         */
        getElement: function() {
            //im going to simply just use the path as the id name to differentiate with ease
            var pathName =this.imageModel.getPath();
            var curIR = document.getElementById(pathName);
            if(curIR == null || curIR =="") {
                var parent = imageCollectionView.getElement();//TODO this is not tru mvc if possible to have >1 collection
                curIR = document.createElement('div');
                if(this.curView==LIST_VIEW) {
                    curIR.className= "imageDivList";
                } else {
                    curIR.className= "imageDiv";
                }
                curIR.setAttribute("id", pathName);
                parent.appendChild(curIR);
            }
            return curIR;
        },

        /**
         * Returns the ImageModel represented by this ImageRenderer.
         */
        getImageModel: function() {
            return this.imageModel;
        },

        /**
         * Sets the ImageModel represented by this ImageRenderer, changing the element and its
         * contents as necessary.
         */
        setImageModel: function(imageModel) {
            this.imageModel=imageModel;
            this.setToView(imageCollectionView.getCurrentView());
        },

        /**
         * Changes the rendering of the ImageModel to either list or grid view.
         * @param viewType A string, either LIST_VIEW or GRID_VIEW
         */
        setToView: function(viewType) {
            this.curView=viewType;
            this.starListener=0;
            this.updateImage();
        },

        /**
         * Returns a string of either LIST_VIEW or GRID_VIEW indicating which view type it is
         * currently rendering.
         */
        getCurrentView: function() {
            return this.curView;
        },
        
        updateImage: function() {
            //var mainDiv =
            var curIR = this.getElement();
            curIR.innerHtml="";//clear the current contents if any
            var img = document.createElement('img');
            img.className="image";
            img.src = this.imageModel.getPath().replace("/i","i");
            curIR.appendChild(img);
            var starDiv = document.createElement('div');
            starDiv.setAttribute('id', "stars");
            curIR.appendChild(starDiv);
            var star1 = document.createElement('img');
            star1.className="ratingStars";
            var star2 = document.createElement('img');
            star2.className="ratingStars";
            var star3 = document.createElement('img');
            star3.className="ratingStars";
            var star4 = document.createElement('img');
            star4.className="ratingStars";
            var star5 = document.createElement('img');
            star5.className="ratingStars";
            starDiv.appendChild(star1);
            starDiv.appendChild(star2);
            starDiv.appendChild(star3);
            starDiv.appendChild(star4);
            starDiv.appendChild(star5);
            this.updateRatingStars(starDiv, this.imageModel.getRating());
            //console.log("star listener is "+ this.starListener);
            if(this.starListener==0) {
                //attach event listeners for hovering
                var thisThing =this;
                star1.addEventListener('click', function() {
                    if(thisThing.imageModel.getRating() == 1) {
                        thisThing.imageModel.setRating(0);
                    } else {
                        thisThing.imageModel.setRating(1);
                    }
                    thisThing.updateRatingStars(starDiv, thisThing.imageModel.getRating());
                });
                star2.addEventListener('click', function() {
                    if(thisThing.imageModel.getRating() == 2) {
                        thisThing.imageModel.setRating(0);
                    } else {
                        thisThing.imageModel.setRating(2);
                    }
                    thisThing.updateRatingStars(starDiv, thisThing.imageModel.getRating());
                });
                star3.addEventListener('click', function() {
                    if(thisThing.imageModel.getRating() == 3) {
                        thisThing.imageModel.setRating(0);
                    } else {
                        thisThing.imageModel.setRating(3);
                    }
                    thisThing.updateRatingStars(starDiv, thisThing.imageModel.getRating());
                });
                star4.addEventListener('click', function() {
                    if(thisThing.imageModel.getRating() == 4) {
                        thisThing.imageModel.setRating(0);
                    } else {
                        thisThing.imageModel.setRating(4);
                    }
                    thisThing.updateRatingStars(starDiv, thisThing.imageModel.getRating());
                });
                star5.addEventListener('click', function() {
                    if(thisThing.imageModel.getRating() == 5) {
                        thisThing.imageModel.setRating(0);
                    } else {
                        thisThing.imageModel.setRating(5);
                    }
                    thisThing.updateRatingStars(starDiv, thisThing.imageModel.getRating());
                });
                //now for hover listeners....
                star1.addEventListener('mouseover', function() {
                    thisThing.updateRatingStars(starDiv, 1);
                });
                star1.addEventListener('mouseout', function() {
                    thisThing.updateRatingStars(starDiv, thisThing.imageModel.getRating());
                });
                star2.addEventListener('mouseover', function() {
                    thisThing.updateRatingStars(starDiv, 2);
                });
                star2.addEventListener('mouseout', function() {
                    thisThing.updateRatingStars(starDiv, thisThing.imageModel.getRating());
                });
                star3.addEventListener('mouseover', function() {
                    thisThing.updateRatingStars(starDiv, 3);
                });
                star3.addEventListener('mouseout', function() {
                    thisThing.updateRatingStars(starDiv, thisThing.imageModel.getRating());
                });
                star4.addEventListener('mouseover', function() {
                    thisThing.updateRatingStars(starDiv, 4);
                });
                star4.addEventListener('mouseout', function() {
                    thisThing.updateRatingStars(starDiv, thisThing.imageModel.getRating());
                });
                star5.addEventListener('mouseover', function() {
                    thisThing.updateRatingStars(starDiv, 5);
                });
                star5.addEventListener('mouseout', function() {
                    thisThing.updateRatingStars(starDiv, thisThing.imageModel.getRating());
                });
                this.starListener=1;
            }
            /*var date = new Date();
            var month = date.getMonth()+1;
            var day = date.getDate();
            var year = date.getYear();
            var mins = date.getMinutes();
            var hours = date.getHours();
            var label = day+"/"+month+"/"+year+" at "+hours+":"+mins;*/
            var modLabel = document.createElement('span');
            var label = this.imageModel.getModificationDate().toString();
            var flabel= label.replace("GMT-0500 (EST)", "");
            modLabel.innerText = flabel;
            curIR.appendChild(modLabel);
        },
        
        updateRatingStars: function(starDiv, rating) {
            var nodes = starDiv.childNodes;
            if(rating==0) {
                nodes[0].src="star-empty.png";
                nodes[1].src="star-empty.png";
                nodes[2].src="star-empty.png";
                nodes[3].src="star-empty.png";
                nodes[4].src="star-empty.png";
            } else if(rating==1){
                nodes[0].src="star-full.png";
                nodes[1].src="star-empty.png";
                nodes[2].src="star-empty.png";
                nodes[3].src="star-empty.png";
                nodes[4].src="star-empty.png";
            } else if(rating==2){
                nodes[0].src="star-full.png";
                nodes[1].src="star-full.png";
                nodes[2].src="star-empty.png";
                nodes[3].src="star-empty.png";
                nodes[4].src="star-empty.png";
            } else if(rating==3){
                nodes[0].src="star-full.png";
                nodes[1].src="star-full.png";
                nodes[2].src="star-full.png";
                nodes[3].src="star-empty.png";
                nodes[4].src="star-empty.png";
            } else if(rating==4){
                nodes[0].src="star-full.png";
                nodes[1].src="star-full.png";
                nodes[2].src="star-full.png";
                nodes[3].src="star-full.png";
                nodes[4].src="star-empty.png";
            } else if(rating==5){
                nodes[0].src="star-full.png";
                nodes[1].src="star-full.png";
                nodes[2].src="star-full.png";
                nodes[3].src="star-full.png";
                nodes[4].src="star-full.png";
            }
        }
    });

    /**
     * A factory is an object that creates other objects. In this case, this object will create
     * objects that fulfill the ImageRenderer class's contract defined above.
     */
    var ImageRendererFactory = function() {
    };

    _.extend(ImageRendererFactory.prototype, {

        /**
         * Creates a new ImageRenderer object for the given ImageModel
         */
        createImageRenderer: function(imageModel) {
            if(imageModel != null) {
                new ImageRenderer(imageModel);
            }
        }
    });

    /**
     * An object representing a DOM element that will render an ImageCollectionModel.
     * Multiple such objects can be created and added to the DOM (i.e., you shouldn't
     * assume there is only one ImageCollectionView that will ever be created).
     */
    var ImageCollectionView = function() {
        this.curView;//defaults to list view
        this.curFactory;
        this.curModel;
        icvCount++;//TODO verify this
        this.icvNum=icvCount;
        this.initCollection();
    };

    _.extend(ImageCollectionView.prototype, {
        /**
         * Returns an element that can be attached to the DOM to display the ImageCollectionModel
         * this object represents.
         */
        getElement: function() {
            var str1 = "icv";
            var str2 = this.icvNum.toString();
            var finalStr =  str1.concat(str2);
            var icvElement = document.getElementById(finalStr);
            if(icvElement == null || icvElement =="") {//create one!
                icvElement = document.createElement('div');
                icvElement.className = "";//TODO update if necessary
                icvElement.setAttribute("id", finalStr);
                appContainer.appendChild(icvElement);
            }
            return icvElement;
        },

        /**
         * Gets the current ImageRendererFactory being used to create new ImageRenderer objects.
         */
        getImageRendererFactory: function() {
            return this.curFactory;
        },

        /**
         * Sets the ImageRendererFactory to use to render ImageModels. When a *new* factory is provided,
         * the ImageCollectionView should redo its entire presentation, replacing all of the old
         * ImageRenderer objects with new ImageRenderer objects produced by the factory.
         */
        setImageRendererFactory: function(imageRendererFactory) {
            this.curFactory=imageRendererFactory;
        },

        /**
         * Returns the ImageCollectionModel represented by this view.
         */
        getImageCollectionModel: function() {
            return this.curModel;
        },

        /**
         * Sets the ImageCollectionModel to be represented by this view. When setting the ImageCollectionModel,
         * you should properly register/unregister listeners with the model, so you will be notified of
         * any changes to the given model.
         */
        setImageCollectionModel: function(imageCollectionModel) {
            this.curModel=imageCollectionModel;
        },

        /**
         * Changes the presentation of the images to either grid view or list view.
         * @param viewType A string of either LIST_VIEW or GRID_VIEW.
         */
        setToView: function(viewType) {
            console.log("changing view!");
            this.curView=viewType;
            this.getElement().innerHTML="";
            //TODO graphical update stuff!
            //loop through all our renders and update!
            var myFact = this.curFactory;
            _.each(this.getImageCollectionModel().getImageModels(), function(imageModel) {
                this.createImageRenderer(imageModel);
            },myFact);
        },

        /**
         * Returns a string of either LIST_VIEW or GRID_VIEW indicating which view type is currently
         * being rendered.
         */
        getCurrentView: function() {
            return this.curView;
        },
        
        filterView: function(filter){
            this.getElement().innerHTML="";
            var myFact = this.curFactory;
            _.each(this.getImageCollectionModel().getImageModels(), function(imageModel) {
                if(imageModel.getRating()==filter || filter==0) {
                    this.createImageRenderer(imageModel);
                }
            },myFact);
        },
        
        /* Initializes the necessary divs in the app-container for everything to be rendered in
        *
        */
        initCollection: function() {
            var mainDiv = document.getElementById('app-container');
            var newCol = document.createElement('div');
            //newCol.className('classNameHere');
            var str1 = "icv";
            var str2 = this.icvNum.toString();
            var finalStr =  str1.concat(str2);
            newCol.setAttribute("id", finalStr);
            mainDiv.appendChild(newCol);
        }
    });

    /**
     * An object representing a DOM element that will render the toolbar to the screen.
     */
    var Toolbar = function() {
        this.listeners = [];
        this.curView=LIST_VIEW;
        this.curRating=0;
        this.toolSize= "Big"; //Big vs Small
    };

    _.extend(Toolbar.prototype, {
        /**
         * Returns an element representing the toolbar, which can be attached to the DOM.
         */
        getElement: function() {
            var curTool = document.getElementById("toolbar");
            return curTool;
        },

        /**
         * Registers the given listener to be notified when the toolbar changes from one
         * view type to another.
         * @param listener_fn A function with signature (toolbar, eventType, eventDate), where
         *                    toolbar is a reference to this object, eventType is a string of
         *                    either, LIST_VIEW, GRID_VIEW, or RATING_CHANGE representing how
         *                    the toolbar has changed (specifically, the user has switched to
         *                    a list view, grid view, or changed the star rating filter).
         *                    eventDate is a Date object representing when the event occurred.
         */
        addListener: function(listener_fn) {
            this.listeners.push(listener_fn);
        },

        /**
         * Removes the given listener from the toolbar.
         */
        removeListener: function(listener_fn) {
            var index = this.listeners.lastIndexOf(listener_fn);
            if(index > -1) {
                this.listeners.splice(index,1);
            }
        },

        /**
         * Sets the toolbar to either grid view or list view.
         * @param viewType A string of either LIST_VIEW or GRID_VIEW representing the desired view.
         */
        setToView: function(viewType) {
            this.curView=viewType;
            var tools = this;
            var date = new Date();
            _.each(this.listeners, function(listener_fn) {
                listener_fn(tools, viewType, date);
            });
        },

        /**
         * Returns the current view selected in the toolbar, a string that is
         * either LIST_VIEW or GRID_VIEW.
         */
        getCurrentView: function() {
            return this.curView;
        },

        /**
         * Returns the current rating filter. A number in the range [0,5], where 0 indicates no
         * filtering should take place.
         */
        getCurrentRatingFilter: function() {
            return this.curRating;
        },

        /**
         * Sets the rating filter.
         * @param rating An integer in the range [0,5], where 0 indicates no filtering should take place.
         */
        setRatingFilter: function(rating) {
            this.curRating=rating;
            var tools = this;
            var date = new Date();
            _.each(this.listeners, function(listener_fn) {
                listener_fn(tools, this.RATING_CHANGE, date);
            });
            console.log("rating filter set");
            imageCollectionView.filterView(rating);
            
        },
        
        ratingStarShade: function(rating) {
            var star1 = document.getElementById("filterStar1");
            var star2 = document.getElementById("filterStar2");
            var star3 = document.getElementById("filterStar3");
            var star4 = document.getElementById("filterStar4");
            var star5 = document.getElementById("filterStar5");
            var menuStar0 = document.getElementById("menuStar0");
            var menuStar1 = document.getElementById("menuStar1");
            var menuStar2 = document.getElementById("menuStar2");
            var menuStar3 = document.getElementById("menuStar3");
            var menuStar4 = document.getElementById("menuStar4");
            var menuStar5 = document.getElementById("menuStar5");
            if(rating==-1){
                rating=this.curRating;
            }
                if(rating==0) {
                    star1.src="star-empty.png";
                    star2.src="star-empty.png";
                    star3.src="star-empty.png";
                    star4.src="star-empty.png";
                    star5.src="star-empty.png";
                    menuStar0.className="current-menu-item";
                    menuStar1.className="";
                    menuStar2.className="";
                    menuStar3.className="";
                    menuStar4.className="";
                    menuStar5.className="";
                } else if(rating==1){
                    star1.src="star-full.png";
                    star2.src="star-empty.png";
                    star3.src="star-empty.png";
                    star4.src="star-empty.png";
                    star5.src="star-empty.png";
                    menuStar1.className="current-menu-item";
                    menuStar0.className="";
                    menuStar2.className="";
                    menuStar3.className="";
                    menuStar4.className="";
                    menuStar5.className="";
                } else if(rating==2){
                    star1.src="star-full.png";
                    star2.src="star-full.png";
                    star3.src="star-empty.png";
                    star4.src="star-empty.png";
                    star5.src="star-empty.png";
                    menuStar2.className="current-menu-item";
                    menuStar1.className="";
                    menuStar0.className="";
                    menuStar3.className="";
                    menuStar4.className="";
                    menuStar5.className="";
                } else if(rating==3){
                    star1.src="star-full.png";
                    star2.src="star-full.png";
                    star3.src="star-full.png";
                    star4.src="star-empty.png";
                    star5.src="star-empty.png";
                    menuStar3.className="current-menu-item";
                    menuStar1.className="";
                    menuStar2.className="";
                    menuStar0.className="";
                    menuStar4.className="";
                    menuStar5.className="";
                } else if(rating==4){
                    star1.src="star-full.png";
                    star2.src="star-full.png";
                    star3.src="star-full.png";
                    star4.src="star-full.png";
                    star5.src="star-empty.png";
                    menuStar4.className="current-menu-item";
                    menuStar1.className="";
                    menuStar2.className="";
                    menuStar3.className="";
                    menuStar0.className="";
                    menuStar5.className="";
                } else if(rating==5){
                    star1.src="star-full.png";
                    star2.src="star-full.png";
                    star3.src="star-full.png";
                    star4.src="star-full.png";
                    star5.src="star-full.png";
                    menuStar5.className="current-menu-item";
                    menuStar1.className="";
                    menuStar2.className="";
                    menuStar3.className="";
                    menuStar4.className="";
                    menuStar0.className="";
                } else{
                    //error
                }
        },
        
        setToolSize: function() {
            //check window size and update accordingly
            var winWidth = window.innerWidth;
            //console.log("The width is: " + winWidth);
            if(winWidth>=760){
                this.toolSize="Big";
            }else {
                this.toolSize="Small";
            }
        },
        
       
        
        largeButtonHover: function() {
            //if(this.toolSize == "Big"){
                var listButton = document.getElementById("toolList");
                var gridButton = document.getElementById("toolGrid");
                var tb = this;
                globalTView=this.curView;
                listButton.addEventListener('mouseover', function () { 
                    gridButton.className="viewSelector viewSelectorInactive";
                });
                listButton.addEventListener("mouseout", function() {
                    if(tb.getCurrentView()==LIST_VIEW) {
                        gridButton.className="viewSelector viewSelectorInactive";
                    } else {
                        gridButton.className="viewSelector";
                    }
                });
                gridButton.addEventListener("mouseover", function() {
                    listButton.className="viewSelector viewSelectorInactive";
                });
                gridButton.addEventListener("mouseout", function() {
                    if(tb.getCurrentView()==GRID_VIEW) {
                        listButton.className="viewSelector viewSelectorInactive";
                    } else {
                        listButton.className="viewSelector";
                    }
                });
            //} else {
            //console.log("toolSize is small...");
                //remove those listeners?
            //}
        },
        
        showSmallMenu: function() {
            var toolMenu = document.getElementById("menuBar");
            var toolNav = document.getElementById("nav");
            if(toolNav.style.display=="block") {
                toolNav.style.display="none"
            } else  {
                toolNav.style.display="block"
            }
        }
    });

    /**
     * An object that will allow the user to choose images to display.
     * @constructor
     */
    var FileChooser = function() {
        this.listeners = [];
        this._init();
    };

    _.extend(FileChooser.prototype, {
        // This code partially derived from: http://www.html5rocks.com/en/tutorials/file/dndfiles/
        _init: function() {
            var self = this;
            this.fileChooserDiv = document.createElement('div');
            var fileChooserTemplate = document.getElementById('file-chooser');
            this.fileChooserDiv.appendChild(document.importNode(fileChooserTemplate.content, true));
            var fileChooserInput = this.fileChooserDiv.querySelector('.files-input');
            fileChooserInput.addEventListener('change', function(evt) {
                var files = evt.target.files;
                var eventDate = new Date();
                _.each(
                    self.listeners,
                    function(listener_fn) {
                        listener_fn(self, files, eventDate);
                    }
                );
            });
        },

        /**
         * Returns an element that can be added to the DOM to display the file chooser.
         */
        getElement: function() {
            return this.fileChooserDiv;
        },

        /**
         * Adds a listener to be notified when a new set of files have been chosen.
         * @param listener_fn A function with signature (fileChooser, fileList, eventDate), where
         *                    fileChooser is a reference to this object, fileList is a list of files
         *                    as returned by the File API, and eventDate is when the files were chosen.
         */
        addListener: function(listener_fn) {
            if (!_.isFunction(listener_fn)) {
                throw new Error("Invalid arguments to FileChooser.addListener: " + JSON.stringify(arguments));
            }

            this.listeners.push(listener_fn);
        },

        /**
         * Removes the given listener from this object.
         * @param listener_fn
         */
        removeListener: function(listener_fn) {
            if (!_.isFunction(listener_fn)) {
                throw new Error("Invalid arguments to FileChooser.removeListener: " + JSON.stringify(arguments));
            }
            this.listeners = _.without(this.listeners, listener_fn);
        }
    });

    // Return an object containing all of our classes and constants
    return {
        ImageRenderer: ImageRenderer,
        ImageRendererFactory: ImageRendererFactory,
        ImageCollectionView: ImageCollectionView,
        Toolbar: Toolbar,
        FileChooser: FileChooser,

        LIST_VIEW: LIST_VIEW,
        GRID_VIEW: GRID_VIEW,
        RATING_CHANGE: RATING_CHANGE
    };
}


