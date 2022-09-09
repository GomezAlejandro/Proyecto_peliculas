const loadMovies = async(id) => {
    let response;
    let movies1 = '';
    let movies2 = '';
    let movies3 = '';
    let gender = '';

    document.getElementById('container-cards1').innerHTML = '';
    document.getElementById('container-cards2').innerHTML = '';
    document.getElementById('container-cards3').innerHTML = '';

    try {
        if(id === 0) {
            response = await axios.get('https://api.themoviedb.org/3/movie/now_playing', {
                params: {
                    api_key: '7736d7e45b7b4d6a6ef1e5a6aafc161f',
                    language: 'es-MX'
                }
            })
        } else {
            response = await axios.get('https://api.themoviedb.org/3/discover/movie', {
                params: {
                    api_key: '7736d7e45b7b4d6a6ef1e5a6aafc161f',
                    language: 'es-MX',
                    with_genres: id
                }
            })
        }

        if(response.status === 200){
            for(let i=0; i<15; i++){

                console.log(response.data.results[i]);

                if(i>=0 && i<5){
                    movies1 += `
                    <div class="card">
                        <img src="https://image.tmdb.org/t/p/w500/${response.data.results[i].poster_path}" class="card-img-top border " alt="...">
                        <div class="card-body">
                            <section class="d-flex justify-content-between align-items-center">
                                <p class="video-card-text m-0" style="color: rgb(0,186,0)">${response.data.results[i].vote_average} votos</p>
                                <span class="video-card-text text-black p-1">${response.data.results[i].title}</span>
                            </section>
                            <p class="m-0 video-card-text text-black">${response.data.results[i].overview}</p>
                        </div>
                    </div>
                    `;
                }

                if(i>=5 && i<10){
                    movies2 += `
                    <div class="card">
                        <img src="https://image.tmdb.org/t/p/w500/${response.data.results[i].poster_path}" class="card-img-top border " alt="...">
                        <div class="card-body">
                            <section class="d-flex justify-content-between align-items-center">
                                <p class="video-card-text m-0" style="color: rgb(0,186,0)">${response.data.results[i].vote_average} votos</p>
                                <span class="video-card-text text-black p-1">${response.data.results[i].title}</span>
                            </section>
                            <p class="m-0 video-card-text text-black">${response.data.results[i].overview}</p>
                        </div>
                    </div>
                    `;
                }

                if(i>=10 && i<15){
                    movies3 += `
                    <div class="card">
                        <img src="https://image.tmdb.org/t/p/w500/${response.data.results[i].poster_path}" class="card-img-top border " alt="...">
                        <div class="card-body">
                            <section class="d-flex justify-content-between align-items-center">
                                <p class="video-card-text m-0" style="color: rgb(0,186,0)">${response.data.results[i].vote_average} votos</p>
                                <span class="video-card-text text-black p-1">${response.data.results[i].title}</span>
                            </section>
                            <p class="m-0 video-card-text text-black">${response.data.results[i].overview}</p>
                        </div>
                    </div>
                    `;
                }
                
            }
        
            switch(id) {
                case 28: 
                    gender = 'Acción';
                    break;
                    case 12:
                    gender = 'Aventura';
                    break;
                    case 16: 
                    gender = 'Animación';
                    break;
                    case 35: 
                    gender = 'Comedia';
                    break;
                    case 80: 
                    gender = 'Crimen';
                    break;
                    case 99: 
                    gender = 'Documental';
                    break;
                    case 18: 
                    gender = 'Drama';
                    break;
                    case 10751: 
                    gender = 'Familia';
                    break;
                    case 14: 
                    gender = 'Fantasía';
                    break;
                    case 36: 
                    gender = 'Historia';
                    break;
                    case 27: 
                    gender = 'Terror';
                    break;
                    case 10402: 
                    gender = 'Música';
                    break;
                    case 9648: 
                    gender = 'Misterio';
                    break;
                    case 10749: 
                    gender = 'Romance';
                    break;
                    case 878: 
                    gender = 'Ciencia Ficción';
                    break;
                    case 10770: 
                    gender = 'Películas de TV';
                    break;
                    case 53: 
                    gender = 'Suspenso';
                    break;
                    case 10752: 
                    gender = 'Bélica';
                    break;
                    case 37: 
                    gender = 'Western';
                    break;
                    default:
                        gender = 'Estrenos del Cine';

            }

			document.getElementById('container-cards1').innerHTML = movies1;
            document.getElementById('container-cards2').innerHTML = movies2;
            document.getElementById('container-cards3').innerHTML = movies3;
            document.getElementById('tittle-carousel').innerHTML = gender;

		} else if(respuesta.status === 401){
			console.log('Pusiste la llave mal');
		} else if(respuesta.status === 404){
			console.log('La pelicula que buscas no existe');
		} else {
			console.log('Hubo un error y no sabemos que paso');
		}
    } catch(e){
		console.log(e);
	}
}