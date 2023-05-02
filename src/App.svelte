

<script>
       import {onMount} from 'svelte';
       import Prism from 'svelte-prism'
       import "prism-themes/themes/prism-dracula.css";

       let finalScript;
       let url_formulario;
       let nombre_formulario;
       let javscriptdata;
       let pagJavascript;






    function code_return() {
        return `<!DOCTYPE html>
                <html lang='en'>
                <head>
                    <link href='https://fonts.googleapis.com/css?family=Material+Icons|Material+Icons+Outlined' rel='stylesheet'>
                    <style>
                    @import url('https://fonts.googleapis.com/css2?family=Playfair Display&display=swap');


                    .upload-files-container {
                        background-color: #f7fff7;
                        width: 420px;
                        padding: 30px 60px;
                        border-radius: 40px;
                        display: flex;
                        align-items: center;
                        justify-content: center;
                        flex-direction: column;
                        box-shadow: rgba(0, 0, 0, 0.24) 0px 10px 20px, rgba(0, 0, 0, 0.28) 0px 6px 6px;
                    }
                    .drag-file-area {
                        border: 2px dashed var(--color-site);
                        border-radius: 40px;
                        margin: 10px 0 15px;
                        padding: 30px 50px;
                        width: 350px;
                        text-align: center;
                    }
                    .drag-file-area .upload-icon {
                        font-size: 53px;
                    }
                    .drag-file-area h3 {
                        font-size: 29px;
                        margin: 15px 0;
                    }
                    .drag-file-area label {
                        font-size: 22px;
                    }
                    .drag-file-area label .browse-files-text {
                        color: var(--color-site);
                        font-weight: bolder;
                        cursor: pointer;
                    }
                    .browse-files span {
                        position: relative;
                        top: -25px;
                    }
                    .default-file-input {
                        opacity: 0;
                    }
                    .cannot-upload-message , .cannot-upload-message-error {
                        background-color: #ffc6c4;
                        font-size: 21px;
                        display: flex;
                        align-items: center;
                        margin: 5px 0;
                        padding: 5px 10px 5px 30px;
                        border-radius: 5px;
                        color: #BB0000;
                        display: none;
                    }
                    @keyframes fadeIn {
                      0% {opacity: 0;}
                      100% {opacity: 1;}
                    }
                    .cannot-upload-message span, .upload-button-icon , .cannot-upload-message-error  {
                        padding-right: 10px;
                    }
                    .cannot-upload-message span:last-child   , .cannot-upload-message-error span:last-child {
                        padding-left: 20px;
                        cursor: pointer;
                    }
                    .file-block {
                        color: #f7fff7;
                        background-color: var(--color-site);
                        transition: all 1s;
                        width: 390px;
                        position: relative;
                        display: none;
                        flex-direction: row;
                        justify-content: space-between;
                        align-items: center;
                        margin: 10px 0 15px;
                        padding: 10px 20px;
                        border-radius: 25px;
                        cursor: pointer;
                    }
                    .file-info {
                        display: item;
                        align-items: center;
                        font-size: 14px;
                    }
                    .file-icon {
                        margin-right: 10px;
                    }
                    .file-name, .file-size {
                        padding: 0 3px;
                    }
                    .remove-file-icon {
                        cursor: pointer;
                    }
                    .progress-bar {
                        display: flex;
                        position: absolute;
                        bottom: 0;
                        left: 4.5%;
                        width: 0;
                        height: 5px;
                        border-radius: 25px;
                        background-color: #4BB543;
                    }
                    .upload-button ,.upload-button-reload{
                        font-family: var(--font-site);
                        background-color: var(--color-site);
                        color: #f7fff7;
                        display: flex;
                        align-items: center;
                        font-size: 21px;
                        border: none;
                        border-radius: 20px;
                        margin: 10px;
                        padding: 7.5px 50px;
                        cursor: pointer;
                    }

                    :root {
                      --color-site: #0b1b4b   ;
                      --font-site : 'Playfair Display'
                    }
                    </style>
                    <meta charset='UTF-8'>
                    <title>Subir Archivo</title>
                </head>




                <body>
                <form class='form-container' enctype='multipart/form-data'>
                    <div class='upload-files-container'>
                        <div class='drag-file-area'>
                            <span class='material-icons-outlined upload-icon'> file_upload </span>
                            <h3 class='dynamic-message'> Arrastra y suelta tu archivo aquí </h3>
                            <h5 class='dynamic-message'> O         </h5>
                            <label class='label' style='color:#0000'>  O
                                <span class='browse-files'>
                                    <input type='file' class='default-file-input'/>
                                    <span class='browse-files-text'>        busca tu Archivo</span>
                                    <span style='color:#000000'>desde el dispositivo</span>
                                </span>
                            </label>
                        </div>
                        <span class='cannot-upload-message'> <span class='material-icons-outlined'>error</span> Seleccione primero el archivo <span class='material-icons-outlined cancel-alert-button'>cancel</span> </span>
                        <span class='cannot-upload-message-error'> <span class='material-icons-outlined'>error</span> Ocurrio un error al cargar el archivo<span class='material-icons-outlined cancel-alert-button2'>cancel</span> </span>
                        <div class='file-block'>
                            <div class='file-info'> <span class='material-icons-outlined file-icon'>description</span> <span class='file-name'> </span> | <span class='file-size'>  </span>
                                <span class='material-icons remove-file-icon'>delete</span>
                            </div>

                            <div class='progress-bar'> </div>
                        </div>
                        <button type='button' class='upload-button'> Subir </button>
                        <button type='button' class='upload-button-reload' style='display:none'> Nuevo Archivo </button>
                    </div>
                </form>
                `
    }


    function code_js(){
            return `
                        var isAdvancedUpload = function() {
                          var div = document.createElement('div');
                          return (('draggable' in div) || ('ondragstart' in div && 'ondrop' in div)) && 'FormData' in window && 'FileReader' in window;
                        }();

                        let draggableFileArea = document.querySelector('.drag-file-area');
                        let browseFileText = document.querySelector('.browse-files');
                        let uploadIcon = document.querySelector('.upload-icon');
                        let dragDropText = document.querySelector('.dynamic-message');
                        let fileInput = document.querySelector('.default-file-input');
                        let cannotUploadMessage = document.querySelector('.cannot-upload-message');
                        let cannotUploadMessageError = document.querySelector('.cannot-upload-message-error');
                        let cancelAlertButton = document.querySelector('.cancel-alert-button');
                        let cancelAlertButton2 = document.querySelector('.cancel-alert-button2');
                        let uploadedFile = document.querySelector('.file-block');
                        let fileName = document.querySelector('.file-name');
                        let fileSize = document.querySelector('.file-size');
                        let progressBar = document.querySelector('.progress-bar');
                        let removeFileButton = document.querySelector('.remove-file-icon');
                        let uploadButton = document.querySelector('.upload-button');
                        let uploadReload = document.querySelector('.upload-button-reload');
                        let fileFlag = 0;
                        let URLPOST = 'https://g2c0586b3c2559e-gtc.adb.us-ashburn-1.oraclecloudapps.com/ords/lecleire/utilidades//upload/';
                        fileInput.addEventListener('click', () => {
                            fileInput.value = '';

                        });



                        fileInput.addEventListener('change', e => {
                            fileName.innerHTML = fileInput.files[0].name;
                            fileSize.innerHTML = (fileInput.files[0].size/1024).toFixed(1) + ' KB';
                            uploadedFile.style.cssText = 'display: table-cell;';
                            progressBar.style.width = 0;
                            fileFlag = 0;

                        });


                        function uploadChunk(filename, blob,miniType) {

                            var status = 0;
                            var frmData = new FormData();
                            frmData.append('file', blob);
                            var xhr = new XMLHttpRequest();
                            var urlParam = '?FILENAME='+filename+'&FILE_MIMETYPE='+miniType ;
                            xhr.open('POST', URLPOST + urlParam+param_form, true);
                            xhr.data
                            xhr.send(frmData);
                            xhr.onreadystatechange = function() {
                                status = this.status;

                            }

                            return status;
                        }

                        uploadButton.addEventListener('click', () => {

                            let isFileUploaded = fileInput.value;
                            if(isFileUploaded != '') {
                                if (fileFlag == 0) {
                                    fileFlag = 1;
                                    var width = 0;
                                    var id = setInterval(frame, 50);
                                    function frame() {
                                        if (width >= 390) {
                                            clearInterval(id);
                                             var blob = fileInput.files[0];
                                             var filename = fileInput.files[0].name;
                                             var miniType = fileInput.files[0].type;
                                             var status = 0;
                                                 var frmData = new FormData();
                                                 frmData.append('file', blob);
                                                 var xhr = new XMLHttpRequest();
                                                 var urlParam = '?FILENAME='+filename+'&FILE_MIMETYPE='+miniType ;
                                                 xhr.open('POST', URLPOST + urlParam+param_form, true);
                                                 xhr.data
                                                 xhr.send(frmData);
                                                 xhr.onreadystatechange = function() {
                                                     status = this.status;

                                                      if (status == 201){
                                                        uploadIcon.innerHTML = 'check_circle';
                                                        dragDropText.innerHTML = '¡Archivo subido con éxito!';
                                                        uploadReload.style.cssText = 'display: block;';
                                                        uploadButton.style.cssText = 'display: none;';
                                                        uploadButton.innerHTML = '<span class= "material-icons-outlined upload-button-icon"> check_circle </span> Subido';
                                                      }else {
                                                        cannotUploadMessageError.style.cssText = 'display: flex; animation: fadeIn linear 1.5s;';

                                                     }

                                                 }


                                        } else {
                                            width += 5;
                                            progressBar.style.width = width + 'px';
                                        }

                                    }


                                }
                            } else {
                                cannotUploadMessage.style.cssText = 'display: flex; animation: fadeIn linear 1.5s;';
                            }
                        });

                        uploadReload.addEventListener('click', () => {
                         location.reload();
                        });

                        cancelAlertButton.addEventListener('click', () => {
                            cannotUploadMessage.style.cssText = 'display: none;';

                        });
                        cancelAlertButton2.addEventListener('click', () => {
                            cannotUploadMessageError.style.cssText = 'display: none;';

                        });
                        if(isAdvancedUpload) {
                            ['drag', 'dragstart', 'dragend', 'dragover', 'dragenter', 'dragleave', 'drop'].forEach( evt =>
                                draggableFileArea.addEventListener(evt, e => {
                                    e.preventDefault();
                                    e.stopPropagation();
                                })
                            );
                            ['dragover', 'dragenter'].forEach( evt => {
                                draggableFileArea.addEventListener(evt, e => {
                                    e.preventDefault();
                                    e.stopPropagation();
                                    uploadIcon.innerHTML = 'file_download';
                                    dragDropText.innerHTML ='¡Coloca tu archivo aquí!';
                                });
                            });

                            draggableFileArea.addEventListener('drop', e => {
                                uploadButton.innerHTML = 'Subir';
                                let files = e.dataTransfer.files;
                                fileInput.files = files;

                                fileName.innerHTML = files[0].name;
                                fileSize.innerHTML = (files[0].size/1024).toFixed(1) + ' KB';
                                uploadedFile.style.cssText = 'display: flex;';
                                progressBar.style.width = 0;
                                fileFlag = 0;
                            });
                        }
                        removeFileButton.addEventListener('click', () => {

                            uploadedFile.style.cssText = 'display: none;';
                            fileName.innerHTML = '';
                            fileSize.innerHTML = ' KB';
                            fileInput.value = '';
                            uploadIcon.innerHTML = 'file_upload';
                            dragDropText.innerHTML = 'Arrastra y suelta tu archivo aquí';
                            uploadButton.innerHTML = 'Subir';
                        });
                        `+ ` var param_form = '&FRMNAME=`+nombre_formulario+`&URL=`+url_formulario
                        + `';`


    }

    function incrementCount() {
            try {
                navigator.clipboard.writeText(finalScript+"\n"+javscriptdata);
                console.log('Content copied to clipboard');
            } catch (err) {
                console.error('Failed to copy: ', err);
            }
        }



    function handleFormSubmit(event) {
        event.preventDefault();
        //Generar la llamada para cargar el codigo al pre

        //finalScript = pagina_generar;
        console.log(nombre_formulario);
        if ((nombre_formulario !=undefined && url_formulario != undefined )){
          finalScript = code_return();
          pagJavascript = code_js();
          javscriptdata = "<script>" + pagJavascript + "\n"+  "<" + "/" + "script>\n</body>\n</html>"

          nombre_formulario = undefined;
          url_formulario =undefined;
        }else{
            alert("Favor llenar los campos solicitados");
        }
    }
</script>
<main>

    <div class="bg-white">
        <header class="absolute inset-x-0 top-0 z-50">
            <nav class="flex items-center justify-between p-6 lg:px-8" aria-label="Global">
                <div class="flex lg:flex-1">
                    <a href="#" class="-m-1.5 p-1.5">
                        <img class="h-8 w-auto" src="https://pbs.twimg.com/profile_images/1142331447816130560/4uWxGsL6_400x400.png" alt="">
                    </a>
                </div>
            </nav>
            <!-- Mobile menu, show/hide based on menu open state. -->

        </header>



        <div class="relative isolate px-2 pt-2 lg:px-2">
            <div class="absolute inset-x-0 -top-40 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80">
                <svg class="relative left-[calc(50%-11rem)] -z-10 h-[21.1875rem] max-w-none -translate-x-1/2 rotate-[30deg] sm:left-[calc(50%-30rem)] sm:h-[42.375rem]" viewBox="0 0 1155 678">
                    <path fill="url(#45de2b6b-92d5-4d68-a6a0-9b9b2abad533)" fill-opacity=".3" d="M317.219 518.975L203.852 678 0 438.341l317.219 80.634 204.172-286.402c1.307 132.337 45.083 346.658 209.733 145.248C936.936 126.058 882.053-94.234 1031.02 41.331c119.18 108.451 130.68 295.337 121.53 375.223L855 299l21.173 362.054-558.954-142.079z" />
                    <defs>
                        <linearGradient id="45de2b6b-92d5-4d68-a6a0-9b9b2abad533" x1="1155.49" x2="-78.208" y1=".177" y2="474.645" gradientUnits="userSpaceOnUse">
                            <stop stop-color="#9089FC" />
                            <stop offset="1" stop-color="#FF80B5" />
                        </linearGradient>
                    </defs>
                </svg>
            </div>
            <div class="mx-auto max-w-2xl py-25 sm:py-20 lg:py-25">

                <div class="text-center">
                    <h1 class="text-4xl font-bold tracking-tight text-gray-900 sm:text-6xl">Generar Formulario</h1>

                    <br>

                    <form on:submit={handleFormSubmit}>
                        <dd class="text-base font-semibold leading-7"> Nombre del Formulario</dd>
                        <input  class="block w-full text-sm text-gray-900 border border-gray-300 rounded-lg cursor-pointer bg-gray-50 dark:text-gray-400 focus:outline-none dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400" type="text" bind:value={nombre_formulario}/>
                        <dd class="text-base font-semibold leading-7 "> URL</dd>
                        <input  class="block w-full text-sm text-gray-900 border border-gray-300 rounded-lg cursor-pointer bg-gray-50 dark:text-gray-400 focus:outline-none dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400" type="text" bind:value={url_formulario}/>
                        <div class="mx-auto mt-5 max-w-2xl sm:mt-5 lg:mt-5 lg:max-w-4xl">
                            <button class="rounded-md bg-indigo-600 px-5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-3 focus-visible:outline-offset-2 focus-visible:outline-indigo-600" type="submit">Generar Codigo</button>
                        </div>
                    </form>

                    <div class="mx-auto mt-16 max-w-2xl sm:mt-20 lg:mt-24 lg:max-w-4xl">
                        <dl class="grid max-w-xl grid-cols-1 gap-y-10 gap-x-8 lg:max-w-none lg:grid-cols-2 lg:gap-y-16">
                            <div class="relative pl-16">
                                <dt class="text-base font-semibold leading-7 text-gray-900">
                                    <div class="absolute top-0 left-0 flex h-10 w-10 items-center justify-center rounded-lg">
                                        <svg width="800px" height="800px" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                            <g id="Edit / Copy">
                                                <path id="Vector" d="M9 9V6.2002C9 5.08009 9 4.51962 9.21799 4.0918C9.40973 3.71547 9.71547 3.40973 10.0918 3.21799C10.5196 3 11.0801 3 12.2002 3H17.8002C18.9203 3 19.4801 3 19.9079 3.21799C20.2842 3.40973 20.5905 3.71547 20.7822 4.0918C21.0002 4.51962 21.0002 5.07967 21.0002 6.19978V11.7998C21.0002 12.9199 21.0002 13.48 20.7822 13.9078C20.5905 14.2841 20.2839 14.5905 19.9076 14.7822C19.4802 15 18.921 15 17.8031 15H15M9 9H6.2002C5.08009 9 4.51962 9 4.0918 9.21799C3.71547 9.40973 3.40973 9.71547 3.21799 10.0918C3 10.5196 3 11.0801 3 12.2002V17.8002C3 18.9203 3 19.4801 3.21799 19.9079C3.40973 20.2842 3.71547 20.5905 4.0918 20.7822C4.5192 21 5.07899 21 6.19691 21H11.8036C12.9215 21 13.4805 21 13.9079 20.7822C14.2842 20.5905 14.5905 20.2839 14.7822 19.9076C15 19.4802 15 18.921 15 17.8031V15M9 9H11.8002C12.9203 9 13.4801 9 13.9079 9.21799C14.2842 9.40973 14.5905 9.71547 14.7822 10.0918C15 10.5192 15 11.079 15 12.1969L15 15" stroke="#000000" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                                            </g>
                                        </svg>
                                    </div>
                                    Copia el codigo
                                </dt>
                                <dd class="mt-2 text-base leading-7 text-gray-600">Copia el codigo generado</dd>
                            </div>

                            <div class="relative pl-16">
                                <dt class="text-base font-semibold leading-7 text-gray-900">
                                    <div class="absolute top-0 left-0 flex h-10 w-10 items-center justify-center rounded-lg">
                                        <svg fill="#000000" width="800px" height="800px" viewBox="0 0 32 32" id="icon" xmlns="http://www.w3.org/2000/svg"><defs><style>.cls-1{fill:none;}</style></defs><title>script</title><polygon points="18.83 26 21.41 23.42 20 22 16 26 20 30 21.42 28.59 18.83 26"/><polygon points="27.17 26 24.59 28.58 26 30 30 26 26 22 24.58 23.41 27.17 26"/><path d="M14,28H8V4h8v6a2.0058,2.0058,0,0,0,2,2h6v6h2V10a.9092.9092,0,0,0-.3-.7l-7-7A.9087.9087,0,0,0,18,2H8A2.0058,2.0058,0,0,0,6,4V28a2.0058,2.0058,0,0,0,2,2h6ZM18,4.4,23.6,10H18Z"/><rect id="_Transparent_Rectangle_" data-name="&lt;Transparent Rectangle&gt;" class="cls-1" width="32" height="32"/></svg>
                                    </div>
                                    Pega el codigo generado
                                </dt>
                                <dd class="mt-2 text-base leading-7 text-gray-600">Pega el script generado a eloqua</dd>
                            </div>

                        </dl>
                    </div>



                    {#if finalScript}

                        <br>
                        <br>
                        <button class="rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600" on:click={incrementCount}>
                            Copiar codigo
                        </button>

                        <div class="relative isolate px-6 pt-14 lg:px-8">
                            <Prism language="markup">
                            <code language="markup">
                                {`${finalScript}`}
                            </code>
                             <code language="javascript">
                                {`${javscriptdata}`}
                             </code>
                            </Prism>
                        </div>
                    {/if}



                </div>
            </div>

            <div class="absolute inset-x-0 top-[calc(100%-13rem)] -z-10 transform-gpu overflow-hidden blur-3xl sm:top-[calc(100%-30rem)]">
                <svg class="relative left-[calc(50%+3rem)] h-[21.1875rem] max-w-none -translate-x-1/2 sm:left-[calc(50%+36rem)] sm:h-[42.375rem]" viewBox="0 0 1155 678">
                    <path fill="url(#ecb5b0c9-546c-4772-8c71-4d3f06d544bc)" fill-opacity=".3" d="M317.219 518.975L203.852 678 0 438.341l317.219 80.634 204.172-286.402c1.307 132.337 45.083 346.658 209.733 145.248C936.936 126.058 882.053-94.234 1031.02 41.331c119.18 108.451 130.68 295.337 121.53 375.223L855 299l21.173 362.054-558.954-142.079z" />
                    <defs>
                        <linearGradient id="ecb5b0c9-546c-4772-8c71-4d3f06d544bc" x1="1155.49" x2="-78.208" y1=".177" y2="474.645" gradientUnits="userSpaceOnUse">
                            <stop stop-color="#9089FC" />
                            <stop offset="1" stop-color="#FF80B5" />
                        </linearGradient>
                    </defs>
                </svg>
            </div>


        </div>

    </div>


</main>

