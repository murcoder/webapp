<template>
  <svg
    v-if="name == 'van'"
    aria-hidden="true"
    data-prefix="fas"
    data-icon="shuttle-van"
    class="svg-inline--fa fa-shuttle-van fa-w-20"
    role="img"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 640 512"
  ><path d="M628.88 210.65L494.39 49.27A48.01 48.01 0 0 0 457.52 32H32C14.33 32 0 46.33 0 64v288c0 17.67 14.33 32 32 32h32c0 53.02 42.98 96 96 96s96-42.98 96-96h128c0 53.02 42.98 96 96 96s96-42.98 96-96h32c17.67 0 32-14.33 32-32V241.38c0-11.23-3.94-22.1-11.12-30.73zM64 192V96h96v96H64zm96 240c-26.51 0-48-21.49-48-48s21.49-48 48-48 48 21.49 48 48-21.49 48-48 48zm160-240h-96V96h96v96zm160 240c-26.51 0-48-21.49-48-48s21.49-48 48-48 48 21.49 48 48-21.49 48-48 48zm-96-240V96h66.02l80 96H384z" /></svg>
  <svg
    v-else-if="name == 'calendar'"
    aria-hidden="true"
    data-prefix="fas"
    data-icon="calendar-alt"
    class="svg-inline--fa fa-calendar-alt fa-w-14"
    role="img"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 448 512"
  ><path d="M0 464c0 26.5 21.5 48 48 48h352c26.5 0 48-21.5 48-48V192H0v272zm320-196c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12h-40c-6.6 0-12-5.4-12-12v-40zm0 128c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12h-40c-6.6 0-12-5.4-12-12v-40zM192 268c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12h-40c-6.6 0-12-5.4-12-12v-40zm0 128c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12h-40c-6.6 0-12-5.4-12-12v-40zM64 268c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12H76c-6.6 0-12-5.4-12-12v-40zm0 128c0-6.6 5.4-12 12-12h40c6.6 0 12 5.4 12 12v40c0 6.6-5.4 12-12 12H76c-6.6 0-12-5.4-12-12v-40zM400 64h-48V16c0-8.8-7.2-16-16-16h-32c-8.8 0-16 7.2-16 16v48H160V16c0-8.8-7.2-16-16-16h-32c-8.8 0-16 7.2-16 16v48H48C21.5 64 0 85.5 0 112v48h448v-48c0-26.5-21.5-48-48-48z" /></svg>
  <svg
    v-else-if="name == 'check'"
    aria-hidden="true"
    data-prefix="fas"
    data-icon="clipboard-check"
    class="svg-inline--fa fa-clipboard-check fa-w-12"
    role="img"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 384 512"
  ><path d="M336 64h-80c0-35.3-28.7-64-64-64s-64 28.7-64 64H48C21.5 64 0 85.5 0 112v352c0 26.5 21.5 48 48 48h288c26.5 0 48-21.5 48-48V112c0-26.5-21.5-48-48-48zM192 40c13.3 0 24 10.7 24 24s-10.7 24-24 24-24-10.7-24-24 10.7-24 24-24zm121.2 231.8l-143 141.8c-4.7 4.7-12.3 4.6-17-.1l-82.6-83.3c-4.7-4.7-4.6-12.3.1-17L99.1 285c4.7-4.7 12.3-4.6 17 .1l46 46.4 106-105.2c4.7-4.7 12.3-4.6 17 .1l28.2 28.4c4.7 4.8 4.6 12.3-.1 17z" /></svg>
  <svg
    v-else-if="name == 'clock'"
    aria-hidden="true"
    data-prefix="far"
    data-icon="clock"
    class="svg-inline--fa fa-clock fa-w-16"
    role="img"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 512 512"
  ><path d="M256 8C119 8 8 119 8 256s111 248 248 248 248-111 248-248S393 8 256 8zm0 448c-110.5 0-200-89.5-200-200S145.5 56 256 56s200 89.5 200 200-89.5 200-200 200zm61.8-104.4l-84.9-61.7c-3.1-2.3-4.9-5.9-4.9-9.7V116c0-6.6 5.4-12 12-12h32c6.6 0 12 5.4 12 12v141.7l66.8 48.6c5.4 3.9 6.5 11.4 2.6 16.8L334.6 349c-3.9 5.3-11.4 6.5-16.8 2.6z" /></svg>
  <svg
    v-else-if="name == 'hands'"
    aria-hidden="true"
    data-prefix="fas"
    data-icon="hands-helping"
    class="svg-inline--fa fa-hands-helping fa-w-20"
    role="img"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 640 512"
  ><path d="M488 192H336v56c0 39.7-32.3 72-72 72s-72-32.3-72-72V126.4l-64.9 39C107.8 176.9 96 197.8 96 220.2v47.3l-80 46.2C.7 322.5-4.6 342.1 4.3 357.4l80 138.6c8.8 15.3 28.4 20.5 43.7 11.7L231.4 448H368c35.3 0 64-28.7 64-64h16c17.7 0 32-14.3 32-32v-64h8c13.3 0 24-10.7 24-24v-48c0-13.3-10.7-24-24-24zm147.7-37.4L555.7 16C546.9.7 527.3-4.5 512 4.3L408.6 64H306.4c-12 0-23.7 3.4-33.9 9.7L239 94.6c-9.4 5.8-15 16.1-15 27.1V248c0 22.1 17.9 40 40 40s40-17.9 40-40v-88h184c30.9 0 56 25.1 56 56v28.5l80-46.2c15.3-8.9 20.5-28.4 11.7-43.7z" /></svg>
  <svg
    v-else-if="name == 'rocket'"
    aria-hidden="true"
    focusable="false"
    data-prefix="fas"
    data-icon="rocket"
    class="svg-inline--fa fa-rocket fa-w-16"
    role="img"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 512 512"
  ><path d="M505.05 19.1a15.89 15.89 0 0 0-12.2-12.2C460.65 0 435.46 0 410.36 0c-103.2 0-165.1 55.2-211.29 128H94.87A48 48 0 0 0 52 154.49l-49.42 98.8A24 24 0 0 0 24.07 288h103.77l-22.47 22.47a32 32 0 0 0 0 45.25l50.9 50.91a32 32 0 0 0 45.26 0L224 384.16V488a24 24 0 0 0 34.7 21.49l98.7-49.39a47.91 47.91 0 0 0 26.5-42.9V312.79c72.59-46.3 128-108.4 128-211.09.1-25.2.1-50.4-6.85-82.6zM384 168a40 40 0 1 1 40-40 40 40 0 0 1-40 40z" /></svg>
  <svg
    v-else-if="name == 'user'"
    aria-hidden="true"
    focusable="false"
    data-prefix="fas"
    data-icon="rocket"
    class="svg-inline--fa fa-rocket fa-w-16"
    role="img"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 512 512"
  ><path d="M224 256c70.7 0 128-57.3 128-128S294.7 0 224 0 96 57.3 96 128s57.3 128 128 128zm89.6 32h-16.7c-22.2 10.2-46.9 16-72.9 16s-50.6-5.8-72.9-16h-16.7C60.2 288 0 348.2 0 422.4V464c0 26.5 21.5 48 48 48h352c26.5 0 48-21.5 48-48v-41.6c0-74.2-60.2-134.4-134.4-134.4z" /></svg>
  <svg
    v-else-if="name === 'user'"
    aria-hidden="true"
    focusable="false"
    data-prefix="fas"
    data-icon="rocket"
    class="svg-inline--fa fa-rocket fa-w-16"
    role="img"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 512 512"
  ><path d="M224 256c70.7 0 128-57.3 128-128S294.7 0 224 0 96 57.3 96 128s57.3 128 128 128zm89.6 32h-16.7c-22.2 10.2-46.9 16-72.9 16s-50.6-5.8-72.9-16h-16.7C60.2 288 0 348.2 0 422.4V464c0 26.5 21.5 48 48 48h352c26.5 0 48-21.5 48-48v-41.6c0-74.2-60.2-134.4-134.4-134.4z" /></svg>
  <svg
    v-else-if="name == 'arrow'"
    aria-hidden="true"
    focusable="false"
    data-prefix="fas"
    data-icon="arrow-right"
    class="svg-inline--fa fa-arrow-right fa-w-16"
    role="img"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 512 512"
  ><path d="M190.5 66.9l22.2-22.2c9.4-9.4 24.6-9.4 33.9 0L441 239c9.4 9.4 9.4 24.6 0 33.9L246.6 467.3c-9.4 9.4-24.6 9.4-33.9 0l-22.2-22.2c-9.5-9.5-9.3-25 .4-34.3L311.4 296H24c-13.3 0-24-10.7-24-24v-32c0-13.3 10.7-24 24-24h287.4L190.9 101.2c-9.8-9.3-10-24.8-.4-34.3z" /></svg>
  <svg
    v-else-if="name == 'training'"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink"
    version="1.1"
    x="0px"
    y="0px"
    viewBox="0 0 100 125"
    enable-background="new 0 0 100 100"
    xml:space="preserve"
  ><path d="M64.181,83.863c0-1.307-1.058-2.364-2.365-2.364H38.184c-1.306,0-2.365,1.058-2.365,2.364c0,1.304,1.059,2.363,2.365,2.363  h23.632C63.123,86.227,64.181,85.17,64.181,83.863z" /><path d="M40.94,88.698c-1.087,0-1.388,0.665-0.673,1.483l3.958,4.521C44.37,94.867,44.662,95,44.88,95h10.24  c0.218,0,0.51-0.133,0.654-0.297l3.958-4.521c0.716-0.818,0.415-1.483-0.673-1.483H40.94z" /><path d="M21.121,45.404H9.597c-0.938,0-1.698,0.76-1.698,1.698c0,0.938,0.759,1.697,1.698,1.697h11.524V45.404z" /><path d="M90.403,45.403H78.879V48.8h11.524c0.938,0,1.697-0.76,1.697-1.698C92.101,46.164,91.342,45.403,90.403,45.403z" /><path d="M51.698,6.698C51.698,5.762,50.938,5,50,5c-0.937,0-1.698,0.762-1.698,1.698v11.523h3.396V6.698z" /><path d="M52.688,35.356c4.484,1.02,8.04,4.575,9.057,9.058c0.158,0.699,0.777,1.172,1.466,1.172c0.11,0,0.222-0.013,0.334-0.037  c0.81-0.185,1.317-0.989,1.135-1.8c-1.274-5.608-5.719-10.055-11.327-11.327c-0.81-0.184-1.614,0.323-1.798,1.136  C51.369,34.367,51.876,35.172,52.688,35.356z" /><path d="M25.543,47.102c0,6.579,3.122,11.715,6.141,16.681c2.149,3.535,4.204,6.941,5.288,10.861  c-0.688,0.413-1.153,1.158-1.153,2.019c0,1.309,1.059,2.365,2.365,2.365h23.632c1.308,0,2.365-1.057,2.365-2.365  c0-0.86-0.465-1.605-1.152-2.019c1.084-3.92,3.138-7.327,5.288-10.861c3.019-4.967,6.141-10.102,6.141-16.681  c0-13.485-10.972-24.456-24.457-24.456S25.543,33.616,25.543,47.102z M50,26.721c11.237,0,20.381,9.143,20.381,20.381  c0,5.438-2.695,9.869-5.548,14.563c-2.354,3.872-4.747,7.849-5.924,12.636H41.092c-1.176-4.787-3.57-8.765-5.924-12.636  c-2.854-4.692-5.549-9.124-5.549-14.563C29.619,35.864,38.762,26.721,50,26.721z" /><path d="M20.231,76.871c0.663,0.664,1.738,0.664,2.401,0.001l8.149-8.148l-2.401-2.401l-8.149,8.148  C19.567,75.134,19.567,76.208,20.231,76.871z" /><path d="M79.77,17.332c-0.663-0.663-1.737-0.665-2.401-0.001l-8.148,8.148l2.401,2.402l8.148-8.148  C80.434,19.069,80.433,17.995,79.77,17.332z" /><path d="M77.369,76.871c0.663,0.664,1.737,0.663,2.4,0c0.664-0.663,0.664-1.737,0.001-2.401l-8.148-8.148l-2.401,2.401  L77.369,76.871z" /><path d="M20.231,17.332c-0.663,0.663-0.665,1.737-0.001,2.401l8.149,8.148l2.402-2.402l-8.149-8.148  C21.969,16.667,20.894,16.669,20.231,17.332z" /></svg>
  <svg
    v-else-if="name == 'workshop'"
    xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:cc="http://creativecommons.org/ns#"
    xmlns:dc="http://purl.org/dc/elements/1.1/"
    version="1.1"
    x="0px"
    y="0px"
    viewBox="0 0 100 125"
  ><g transform="translate(0,-952.36218)"><path
    fill-rule="nonzero"
    style="baseline-shift:baseline;block-progression:tb;color:#000000;direction:ltr;text-indent:0;enable-background:accumulate;text-transform:none;"
    d="m75.11,960.47c-4.363,0.005-8.462,1.8014-11.688,4.8438-0.0561,0.0363-0.10852,0.0783-0.15625,0.125-3.4347,3.3072-4.9741,7.6277-4.9688,11.844,0.002,1.3928,0.0959,2.8916,0.5,4.375l-8.6875,8.8125-6.9062-7.5c0.4569-1.4775,0.57932-2.9437,0.625-4.3438,0.1376-4.2146-1.264-8.6173-4.5938-12.031-3.1475-3.2266-7.2298-5.1993-11.656-5.3438-1.8233-0.0596-3.6272,0.035-5.5312,0.4375a1.0001,1.0001,0,0,0,-0.53125,1.6562l9.8125,10.469-2.2188,6.4062-6.5625,1.3125-9.8438-9.9375a1.0001,1.0001,0,0,0,-1.5938,0.25c-0.91367,1.7844-1.406,3.7351-1.4687,5.6562-0.13353,4.0943,1.4782,8.18,4.625,11.406,3.1909,3.2396,7.3872,5.2044,11.656,5.3438,1.6297,0.0532,3.2961-0.082,4.9375-0.375l7.75,8.3125-9.25,9.375c-1.8691-0.092-2.5093-0.4123-5.25-0.375-4.2704,0.048-8.4898,1.9219-11.75,5.0938-0.0104-0.0002-0.0208-0.0002-0.0312,0-3.2169,3.1601-4.8899,7.2483-4.8437,11.344,0.0215,1.916,0.4363,3.8821,1.3125,5.6875,0.27534,0.565,1.1417,0.7179,1.5937,0.2813l10.062-9.7188,6.5312,1.4375,2.0938,6.4375-10,10.281c-0.47633,0.5006-0.19926,1.4795,0.46875,1.6562,1.8984,0.4439,3.7106,0.583,5.5312,0.5625,4.4301-0.05,8.5356-1.9672,11.75-5.125,3.4013-3.3412,4.9224-7.689,4.875-11.906,0.001-0.031,0.001-0.062,0-0.094-0.0574-0.4497-0.1789-2.2731-0.875-4.125l8.875-8.9063,9.1875,9.8438-0.375,9.6562a1.0001,1.0001,0,0,0,0.28125,0.7188l8.4062,9.0937a1.0001,1.0001,0,0,0,0.6875,0.3125l12.344,0.4688a1.0001,1.0001,0,0,0,0.71875,-0.25l5.3438-4.9063,3.75-3.4687a1.0001,1.0001,0,0,0,0.34375,-0.7188l0.46875-12.344a1.0001,1.0001,0,0,0,-0.25,-0.7188l-8.3125-8.9687a1.0001,1.0001,0,0,0,-0.0937,-0.125,1.0001,1.0001,0,0,0,-0.5625,-0.2813,1.0001,1.0001,0,0,0,-0.125,-0.031h-0.1875l-11.469-0.4375-8.625-9.375,9.5625-9.5937c1.6226,0.3454,3.2718,0.5331,4.9062,0.53125,4.272-0.005,8.5523-1.83,11.844-4.9688,3.2482-3.1275,4.9741-7.186,4.9688-11.281-0.002-1.9212-0.42499-3.8773-1.2812-5.6875-0.27534-0.56496-1.1417-0.71784-1.5938-0.28125l-10.156,9.5938-6.5-1.5-2-6.5,10.094-10.125c0.50807-0.49766,0.22321-1.5232-0.46875-1.6875-1.8893-0.46171-3.6749-0.59581-5.5-0.59375zm0,2c1.0524-0.001,2.0717,0.20556,3.0938,0.34375l-9.0938,9.0938c-0.25549,0.25499-0.35544,0.65477-0.25,1l2.375,7.5938c0.0983,0.33278,0.38193,0.60409,0.71875,0.6875l7.625,1.75c0.31836,0.0712,0.66944-0.0256,0.90625-0.25l9.4062-8.9062c0.37049,1.1402,0.62355,2.3068,0.625,3.4688,0.005,3.5317-1.4608,7.068-4.3438,9.8438-2.9479,2.8111-6.772,4.4017-10.469,4.4062-1.7046,0.002-3.3894-0.13457-5-0.53125-0.33648-0.0936-0.71958,0.005-0.96875,0.25l-9.8438,9.875-8.4062-9.125,9.125-9.2812c0.25609-0.26722,0.3443-0.68308,0.21875-1.0312-0.46599-1.3304-0.52933-2.8256-0.53125-4.375-0.005-3.7032,1.3334-7.44,4.3125-10.344,0.0217-0.0199,0.0426-0.0408,0.0625-0.0625,2.9203-2.8119,6.5617-4.4014,10.438-4.4062zm-48.375,0.78125c0.25936-0.0137,0.51976-0.009,0.78125,0,3.8744,0.12641,7.4498,1.8473,10.281,4.75,2.9313,3.0054,4.153,6.8039,4.0312,10.531-0.0505,1.5486-0.1488,3.028-0.65625,4.3438a1.0001,1.0001,0,0,0,0.1875,1.0312l27.312,29.688a1.0001,1.0001,0,0,0,0.6875,0.3125l11.656,0.4375,7.8438,8.5-0.4375,11.531-3.4688,3.1875-5.0625,4.625-11.5-0.4375-7.8438-8.5,0.375-9.6562a1.0001,1.0001,0,0,0,-0.25,-0.7188l-28.688-30.687a1.0001,1.0001,0,0,0,-0.9375,-0.3125c-1.6153,0.34451-3.3532,0.43081-5.0625,0.375-3.6955-0.12064-7.4223-1.8161-10.281-4.7188-2.796-2.8666-4.1776-6.4402-4.0625-9.9688,0.0377-1.1543,0.31601-2.3094,0.71875-3.4375l9.125,9.1875a1.0001,1.0001,0,0,0,0.90625,0.28125l7.6875-1.5312a1.0001,1.0001,0,0,0,0.75,-0.65625l2.5938-7.5312a1.0001,1.0001,0,0,0,-0.21875,-1l-8.7812-9.375c0.76525-0.0778,1.5344-0.20879,2.3125-0.25zm13.25,40.406,8.375,8.9687-9.3438,9.375c-0.29244,0.2828-0.38391,0.7533-0.21875,1.125,0.76364,1.5553,0.79415,3.1428,0.90625,4.125,0.004,0.034-0.004,0.093,0,0.125,0.0115,3.688-1.319,7.4338-4.2812,10.344-2.8937,2.8427-6.5002,4.4876-10.375,4.5312-1.0658,0.012-2.0894-0.1848-3.125-0.3125l9-9.1875c0.25549-0.255,0.35544-0.6547,0.25-1l-2.4375-7.5937c-0.11282-0.329-0.409-0.5881-0.75-0.6563l-7.625-1.6875c-0.31836-0.071-0.66944,0.026-0.90625,0.25l-9.3125,9.0313c-0.38161-1.1401-0.64307-2.2972-0.65625-3.4688,0.00016-0.01,0.00016-0.021,0-0.031-0.0398-3.5311,1.3953-7.0707,4.25-9.875,2.9193-2.8402,6.7085-4.4896,10.406-4.5312,2.8006-0.038,3.111,0.345,5.5938,0.4062,0.27882,0.01,0.55833-0.1099,0.75-0.3125l9.5-9.625zm31.438,14.656a1.0001,1.0001,0,0,0,-0.5,0.25l-5.3125,4.9375a1.0001,1.0001,0,0,0,-0.3125,0.6875l-0.28125,7.2813a1.0001,1.0001,0,0,0,0.28125,0.7187l4.9375,5.3125a1.0001,1.0001,0,0,0,0.6875,0.3125l7.25,0.2813a1.0001,1.0001,0,0,0,0.71875,-0.2813l5.3438-4.9375a1.0001,1.0001,0,0,0,0.3125,-0.6875l0.25-7.2812a1.0001,1.0001,0,0,0,-0.25,-0.7188l-4.8438-5.1562a1.0001,1.0001,0,0,0,-0.0312,-0.062,1.0001,1.0001,0,0,0,-0.0937,-0.094,1.0001,1.0001,0,0,0,-0.6875,-0.3125h-0.0312-0.1875l-7.0312-0.25a1.0001,1.0001,0,0,0,-0.21875,0zm0.5625,2,6.4688,0.25,4.3438,4.6875-0.25,6.4375-4.7188,4.375-6.4062-0.2187-4.4062-4.7188,0.25-6.4375,4.7188-4.375z"
  /></g></svg>
  <svg
    v-else-if="name == 'event'"
    xmlns:dc="http://purl.org/dc/elements/1.1/"
    xmlns:cc="http://creativecommons.org/ns#"
    xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
    xmlns:svg="http://www.w3.org/2000/svg"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd"
    xmlns:inkscape="http://www.inkscape.org/namespaces/inkscape"
    version="1.1"
    x="0px"
y="0px" viewBox="0 0 100 125"
  ><g transform="translate(0,-952.36218)"><path
    d="m 91,965.36218 c 2.181399,0 4,1.8186 4,4 l 0,66.00002 c 0,2.1814 -1.818601,4 -4,4 l -70,0 c -0.522,0 -1.0391,-0.2225 -1.4062,-0.5938 l -13.9999995,-14 c -0.3713,-0.367 -0.5896,-0.8842 -0.5938,-1.4062 l 0,-54.00002 c 0,-2.1814 1.8186,-4 4,-4 l 81.9999995,0 z m 0,4 -81.9999995,0 0,16 81.9999995,0 0,-16 z m -18,4 c 2.2091,0 4,1.7908 4,4 0,2.2091 -1.7909,4 -4,4 -2.209101,0 -4,-1.7909 -4,-4 0,-2.2092 1.790899,-4 4,-4 z m -46,0 c 2.209101,0 4,1.7908 4,4 0,2.2091 -1.790899,4 -4,4 -2.2091,0 -4,-1.7909 -4,-4 0,-2.2092 1.7909,-4 4,-4 z m 64,16 -81.9999995,0 0,32.00002 9.9999995,0 c 2.1814,0 4,1.8186 4,4 l 0,10 68,0 0,-46.00002 z m -11,7 0,14.00002 -12,0 0,-14.00002 12,0 z m -16,0 0,14.00002 -12,0 0,-14.00002 12,0 z m -16,0 0,14.00002 -12,0 0,-14.00002 12,0 z m -16,0 0,14.00002 -12,0 0,-14.00002 12,0 z m 48,18.00002 0,14 -12,0 0,-14 12,0 z m -16,0 0,14 -12,0 0,-14 12,0 z m -16,0 0,14 -12,0 0,-14 12,0 z m -29,11 -7.156199,0 7.156199,7.1562 0,-7.1562 z"
    style="text-indent:0;text-transform:none;direction:ltr;block-progression:tb;baseline-shift:baseline;color:#000000;enable-background:accumulate;"
    stroke="none"
    marker="none"
    visibility="visible"
    display="inline"
    overflow="visible"
  /></g></svg>
  <svg
    v-else-if="name == 'meetup'"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink"
    version="1.1"
    x="0px"
    y="0px"
    viewBox="0 0 100 125"
    enable-background="new 0 0 100 100"
    xml:space="preserve"
  ><circle
    cx="35.148"
    cy="24.359"
    r="2.219"
  /><circle
    cx="35.148"
    cy="74.709"
    r="2.219"
  /><circle
    cx="26.119"
    cy="64.762"
    r="1.913"
  /><circle
    cx="74.02"
    cy="18.391"
    r="1.913"
  /><circle
    cx="65.908"
    cy="80.83"
    r="1.913"
  /><circle
    cx="38.209"
    cy="84.35"
    r="1.913"
  /><circle
    cx="19.538"
    cy="35.991"
    r="1.913"
  /><circle
    cx="22.445"
    cy="54.049"
    r="1.913"
  /><circle
    cx="78.917"
    cy="47.315"
    r="1.913"
  /><circle
    cx="54.89"
    cy="78.381"
    r="1.913"
  /><circle
    cx="51.676"
    cy="21.758"
    r="1.913"
  /><circle
    cx="17.089"
    cy="51.753"
    r="2.219"
  /><circle
    cx="75.703"
    cy="64.455"
    r="2.219"
  /><circle
    cx="29.103"
    cy="23.211"
    r="1.683"
  /><circle
    cx="78.075"
    cy="42.8"
    r="1.377"
  /><circle
    cx="80.217"
    cy="74.326"
    r="1.377"
  /><circle
    cx="34.612"
    cy="80.142"
    r="1.377"
  /><circle
    cx="21.298"
    cy="63.308"
    r="1.377"
  /><circle
    cx="49.457"
    cy="16.325"
    r="1.377"
  /><circle
    cx="71.801"
    cy="23.211"
    r="1.684"
  /><circle
    cx="21.91"
    cy="49.228"
    r="1.683"
  /><circle
    cx="42.417"
    cy="78.917"
    r="3.52"
  /><circle
    cx="65.22"
    cy="24.283"
    r="3.52"
  /><circle
    cx="24.359"
    cy="68.664"
    r="1.224"
  /><circle
    cx="62.006"
    cy="82.284"
    r="1.225"
  /><circle
    cx="84.809"
    cy="63.919"
    r="1.224"
  /><circle
    cx="85.268"
    cy="31.628"
    r="1.224"
  /><circle
    cx="65.373"
    cy="18.467"
    r="1.224"
  /><circle
    cx="52.824"
    cy="17.549"
    r="1.224"
  /><circle
    cx="28.338"
    cy="30.557"
    r="1.224"
  /><circle
    cx="33.846"
    cy="83.814"
    r="1.224"
  /><circle
    cx="6.311"
    cy="32.547"
    r="0.918"
  /><circle
    cx="94.144"
    cy="56.88"
    r="0.653"
  /><circle
    cx="19.921"
    cy="6.296"
    r="0.653"
  /><circle
    cx="19.156"
    cy="91.313"
    r="0.653"
  /><circle
    cx="56.037"
    cy="81.825"
    r="0.652"
  /><circle
    cx="82.36"
    cy="53.166"
    r="0.653"
  /><circle
    cx="56.803"
    cy="12.305"
    r="0.653"
  /><circle
    cx="15.33"
    cy="56.38"
    r="0.653"
  /><circle
    cx="30.94"
    cy="74.744"
    r="0.653"
  /><circle
    cx="68.587"
    cy="91.926"
    r="0.652"
  /><circle
    cx="52.211"
    cy="14.03"
    r="0.918"
  /><circle
    cx="89.553"
    cy="69.888"
    r="0.918"
  /><circle
    cx="24.818"
    cy="71.878"
    r="0.918"
  /><circle
    cx="21.145"
    cy="31.628"
    r="0.918"
  /><circle
    cx="56.037"
    cy="17.702"
    r="0.918"
  /><circle
    cx="78.075"
    cy="52.136"
    r="0.918"
  /><circle
    cx="25.889"
    cy="77.233"
    r="0.918"
  /><circle
    cx="72.336"
    cy="30.021"
    r="2.984"
  /><circle
    cx="33.77"
    cy="14.871"
    r="1.607"
  /><circle
    cx="15.712"
    cy="34.459"
    r="1.071"
  /><circle
    cx="66.368"
    cy="87.411"
    r="1.071"
  /><circle
    cx="31.399"
    cy="27.803"
    r="1.607"
  /><circle
    cx="80.677"
    cy="63.919"
    r="1.607"
  /><circle
    cx="11.657"
    cy="55.196"
    r="1.607"
  /><circle
    cx="84.503"
    cy="38.056"
    r="1.147"
  /><circle
    cx="74.555"
    cy="34.842"
    r="1.148"
  /><circle
    cx="83.125"
    cy="67.286"
    r="1.147"
  /><circle
    cx="46.09"
    cy="89.323"
    r="1.148"
  /><circle
    cx="18.696"
    cy="56.114"
    r="1.147"
  /><circle
    cx="28.644"
    cy="18.62"
    r="1.148"
  /><circle
    cx="41.652"
    cy="12.346"
    r="1.147"
  /><circle
    cx="76.544"
    cy="38.668"
    r="1.607"
  /><circle
    cx="46.702"
    cy="21.987"
    r="1.607"
  /><circle
    cx="16.401"
    cy="74.785"
    r="1.071"
  /><circle
    cx="25.047"
    cy="34.613"
    r="2.525"
  /><circle
    cx="32.776"
    cy="19.539"
    r="1.836"
  /><circle
    cx="52.211"
    cy="82.743"
    r="1.836"
  /><circle
    cx="15.329"
    cy="44.178"
    r="1.837"
  /><circle
    cx="80.064"
    cy="35.761"
    r="1.837"
  /><circle
    cx="61.011"
    cy="77.311"
    r="2.525"
  /><circle
    cx="57.797"
    cy="22.216"
    r="2.526"
  /><circle
    cx="29.333"
    cy="70.117"
    r="2.984"
  /><circle
    cx="79.376"
    cy="57.874"
    r="2.984"
  /><circle
    cx="68.586"
    cy="74.633"
    r="3.52"
  /><circle
    cx="21.451"
    cy="42.342"
    r="3.52"
  /><circle
    cx="62.924"
    cy="13.417"
    r="1.53"
  /><circle
    cx="49.151"
    cy="78.764"
    r="1.53"
  /><circle
    cx="14.105"
    cy="21.069"
    r="1.531"
  /><circle
    cx="38.132"
    cy="92.537"
    r="1.53"
  /><circle
    cx="79.682"
    cy="40.045"
    r="0.842"
  /><circle
    cx="75.55"
    cy="25.507"
    r="0.842"
  /><circle
    cx="79.299"
    cy="68.052"
    r="1.684"
  /><circle
    cx="83.048"
    cy="70.348"
    r="0.842"
  /><circle
    cx="88.94"
    cy="49.84"
    r="0.842"
  /><circle
    cx="83.431"
    cy="60.4"
    r="0.842"
  /><circle
    cx="27.19"
    cy="26.731"
    r="0.842"
  /><circle
    cx="46.779"
    cy="7.989"
    r="0.842"
  /><circle
    cx="31.705"
    cy="77.692"
    r="0.841"
  /><circle
    cx="43.381"
    cy="85.977"
    r="2.219"
  /><circle
    cx="47.647"
    cy="82.57"
    r="1.378"
  /><circle
    cx="47.921"
    cy="86.361"
    r="0.842"
  /><circle
    cx="68.739"
    cy="88.252"
    r="0.842"
  /><circle
    cx="18.237"
    cy="47.238"
    r="0.841"
  /><circle
    cx="79.452"
    cy="12.958"
    r="1.683"
  /><circle
    cx="69.199"
    cy="18.927"
    r="1.607"
  /><circle
    cx="75.779"
    cy="10.969"
    r="0.842"
  /><circle
    cx="50.528"
    cy="50.008"
    r="22.726"
  /></svg>
</template>

<script>
export default {
  props: ['name']
}
</script>

<style lang="scss">
</style>
