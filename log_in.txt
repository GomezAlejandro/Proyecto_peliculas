var usuarios = [
    { usuario: "julio", contraseña: "123"},
    { usuario: "marco", contraseña: "123"},
    { usuario: "alex", contraseña: "123"}
]

function login(){
    var user, pass
    user = document.getElementById("usuario").value;
    pass = document.getElementById("contraseña").value;

    let cliente = usuarios.find(x => x.usuario === user && x.contraseña === pass)

    if(cliente){
        localStorage.setItem("cliente", JSON.stringify(cliente))
        window.location="index.html";
    }else{
        alert("Vuelve a Intentar")
    }

}