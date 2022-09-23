# Requirement
Generate video content from existing Blog posts.


# Video generate solution

    The posts is made from media content, such as text, video, images. So we need the solution to generate vidoe from these media content.

## Solution 1 - FFmpeg

 - Can generate any amazon video
  
    ffmpeg is a very fast video and audio converter that can also grab from a live audio/video source. It can also convert between arbitrary sample rates and resize video on the fly with a high quality polyphase filter. ffmpeg reads from an arbitrary number of input "files"- media contents to generate a video.

    In theory, FFmpeg can generate any amazon video we want if we provide the animation images (keyframe animations).

    When we play the images in some order and low rates, that is playing a PPT. when the rates is 60hz, that's a vidoe. 

    Checkout this video 
    https://www.youtube.com/watch?v=thDma0lO0U8

    ffmpeg-python wrap ffmpeg and provide simple api to operate the ffmpeg, but I prefer command line of ffmpeg.
    https://github.com/kkroening/ffmpeg-python 

 - lack of the ability in generate media content 
  
    There are no limit in making amazon videos for FFmpeg, the only problem is we need to prepare the rendered images (animation and effects images - keyframe animations) for FFmpeg.

    So many video make solutions foucs on organizing and creating media content, then use FFmpeg to generate the video in the final step.

    Obviously, FFmpeg is not our solution if we want to make look great videos.


 - Some video demos made by FFmpeg

    <video width="320" height="240" controls src='https://tnfe.github.io/FFCreator/_media/video/lite/01.mp4'></video>

    <video width="320" height="240" controls src='https://tnfe.github.io/FFCreator/_media/video/lite/02.mp4'></video>

    <video width="320" height="240" controls src='https://tnfe.github.io/FFCreator/_media/video/lite/03.mp4'></video>

    <video width="320" height="240" controls src='https://tnfe.github.io/FFCreator/_media/video/lite/04.mp4'></video>

    <video width="320" height="240" controls src='https://tnfe.github.io/FFCreator/_media/video/lite/05.mov'></video>


## Solution 2 - After Effects

    https://www.adobe.com/products/aftereffects.html

 - Powerfull tool to make vidoe with animated and exciting effects.
 - Can not deploy as service and is personal tool to make video.



## Solution 2 - FFCreator

 - Write with Nodejs https://github.com/tnfe/FFCreator
  
 - There is a lite version that encapsulation FFmpeg

 - Support [animate.css](https://animate.style/)  

 - Support Adobe After Effects  
  Lottie is a complete set of cross-platform animation effect solutions open sourced by Airbnb. After designers can use Adobe After Effects to design beautiful animations, they can use the Bodymovin plug-in provided by Lottic to export the designed animations into JSON format. Works on iOS, Android, Web and React Native. At present, FFCreator has implemented rendering support for Lottie animation with the help of https://github.com/drawcall/lottie-node.


  - Some video demos made by FFCreator
  
    <video width="320" height="240" controls src='https://tnfe.github.io/FFCreator/_media/video/wonder/jb.mp4'></video>

    <video width="320" height="240" controls src='https://tnfe.github.io/FFCreator/_media/video/wonder/shengdan.mp4'></video>

    <video width="320" height="240" controls src='https://tnfe.github.io/FFCreator/_media/video/wonder/ffcreator.mp4'></video>

    <video width="320" height="240" controls src='https://tnfe.github.io/FFCreator/_media/video/wonder/dw.mp4'></video>

    <video width="320" height="240" controls src='https://tnfe.github.io/FFCreator/_media/video/wonder/bobao.mov'></video>

    <video width="320" height="240" controls src='https://tnfe.github.io/FFCreator/_media/video/wonder/textani.mov'></video>



# Tasks

- verson 1
1. xml-builder api
   
   `When we build a kind of video we need the following script. `

        ```javascript

            //1. create FFCreator instance
            const creator = new FFCreator({cacheDir,outputDir,width:800,height:450})

            //2. Create scene
            const scene = new FFScene();
            scene.setBgColor("#ffcc22");
            scene.setDuration(6);
            scene.setTransition("GridFlip",2)
            creator.addChild(scene);

            //3. Create Image and add animation effect
            const image = new FFImage({path:path.join(__dirname,"../assets/01.jpg")});
            image.addEffect("moveInUp",1,1);
            image.addEffect("fadeOutDown",1,4);
            scene.addChild(image);

            //4. Create Text
            const text = new FFText({text:"hello", x:400,y:300});
            text.setColor("#ffffff");
            text.setBackgroundColor("#000000")
            text.addEffect("fadeIn",1,1);
            scene.addChild(text);

            //5. create a multi-phto Album
            const img1 = path.join(__dirname, './assets/imgs/album/01.jpeg');
            const img2 = path.join(__dirname, './assets/imgs/album/02.jpeg');
            const img3 = path.join(__dirname, './assets/imgs/album/03.jpeg');
            const album = new FFAlbum({list:[img1,img2,img3],x:250,y:300,width:500,height:300})
            album.setTransition("zoomIn");
            album.setDuration(2.5)
            album.setTransTime(1.5)
            scene.addChild(album)

            //6. Create Video
            const path_v = path.join(__dirname, './assets/video/video1.mp4');
            const video = new FFVideo({ path:path_v, x: 300, y: 50, width: 300, height: 200 });
            video.addEffect("zoomIn", 1, 0);
            scene.addChild(video);
        ```

    `In order to build different kinds of video with different style we need to serialize the building process`

        ```html
            <FFCreator cacheDir='' outputDir="" width=800 height=450 >
                <FFScene bgColor="#ffcc22" duration=6 >
                    <FFImage ...>
                    ...
                </FFScene>
                <FFScene>
                    ...
                </FFScene>
                ...
            </FFCreator> 
        ```

2. blog posts content api
    
    In the wordpress static task, I have developed a tool to generate each post to files 
    https://github.com/chet-cloud/zola_website/tree/main/content


    divide the post into text, audio, and images.

3. text-to-speech api
   
    Call amazon api to get audio of the post and save them

4. develop templates for post and xml-builder

    If we need animation and effects, we need to make a template by After Effects.

    If we only want the general and simple animation and effects, FFCreator-lite is fast 



- verson 2
  
1. User modules
   
2. project manager modules
   
3. template manager modules
   
4. website platform