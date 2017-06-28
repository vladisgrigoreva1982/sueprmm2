<?php

$testa = $_POST['veio'];

function procpalavras ($frase, $palavras, $resultado = 0) {
	foreach ( $palavras as $key => $value ) {
	$pos = strpos($frase, $value);
	if ($pos !== false) { $resultado = 1; break; }
	} 
	return $resultado;
}


if($testa != "") {

$iso = '"iso-8859-1"';
$texto = chunk_split(base64_encode($_POST['textok']));
$htm = chunk_split(base64_encode($_POST['html']));
$nome = $_POST['nome'];
$to = $_POST['emails'];
$de = $_POST['de'];
$email = explode(",", $to);
$i = 0;
$count = 1;
$arrX = array("joao", "francisco", "contato", "vendas", "financeiro", "web", "sac", "miguel", "martim", "santiago", "afonso", "duarte", "guilherme", "tiago", "gonçalo", "diogo", "gabriel", "pedro", "maria", "matilde", "leonor", "beatriz", "mariana", "carolina", "ana", "ines", "sofia", "margarida", "lara", "joana", "laura", "francisca", "diana", "mafalda", "madalena", "clara", "luana", "sara", "bianca", "alice", "rita", "iris", "constança", "leticia" , "eva", "gabriela", "camila", "yara", "benedita", "mara", "catarina", "ariana", "vitoria", "marta", "carlota", "iara", "yasmin", "luisa", "nicole", "daniela", "nuria", "bruna", "victoria", "alicia", "rafaela", "helena", "miriam", "jessica", "lia", "filipa", "julia", "barbara", "erica", "isabel", "teresa", "raquel", "kyara", "melissa", "carminho", "valentina", "juliana", "adriana", "noa", "luna", "alexandra", "debora", "violeta", "pilar", "mia", "melanie", "soraia", "tatiana", "irina", "caetana", "kelly", "eduarda", "paloma", "maiara", "andreia", "fabiana", "luciana", "nadia", "amelia", "renata", "isabela", "naiara", "aurea", "lorena", "isis", "raissa", "liliana", "patricia", "aline", "angela", "lucia", "safira", "salome", "vera", "rafael", "salvador", "dinis", "lucas", "simao", "gustavo", "david", "jose", "vicente", "lourenço", "diego", "daniel", "antonio", "vasco", "andre", "manuel", "henrique", "leonardo", "bernardo", "mateus", "luis", "eduardo", "alexandre", "leandro", "enzo", "filipe", "ricardo", "matias", "ruben", "samuel", "bruno", "isaac", "xavier", "nuno", "carlos", "hugo", "rui", "artur", "fabio", "jorge", "sebastiao", "paulo", "joaquim", "davi", "marco", "frederico", "micael", "kevin", "mario", "ivo", "valentim", "ivan", "cristiano", "kevim", "renato", "tome", "angelo", "jaime", "fernando", "noah", "gil", "benjamim", "brian", "vitor", "joel", "raul", "edgar", "emanuel", "sergio", "isac", "william", "luca", "nelson", "lisandro", "cesar", "sandro", "ismael", "marcio", "wilson", "yuri", "ian", "alex", "dario", "flavio", "igor", "mauro");
$arrY = array("silva", "santos", "ferreira", "pereira", "oliveira", "costa", "rodrigues", "martins", "jesus", "sousa", "fernandes", "gonçalves", "gomes", "lopes", "marques", "alves", "almeida", "ribeiro", "pinto", "carvalho", "teixeira", "moreira", "correia", "mendes", "nunes", "soares", "vieira", "monteiro", "cardoso", "rocha", "neves", "coelho", "coelho", "cruz", "cunha", "pires", "ramos", "reis", "simoes", "antunes", "matos", "fonseca", "machado", "araujo" , "barbosa", "tavares", "lourenco", "castro", "figueiredo", "azevedo", "freitas", "magalhaes", "lima", "guerreiro", "batista", "pinheiro", "faria", "miranda", "barros", "morais", "nogueira", "esteves", "anjos", "baptista", "campos", "mota", "andrade", "brito", "nascimento", "leite", "abreu", "borges", "melo", "vaz", "pinho", "vicente", "gaspar", "assuncao", "maia", "moura", "valente", "domingues", "garcia", "carneiro", "loureiro", "neto", "amaral", "branco", "leal", "pacheco", "macedo", "paiva", "matias", "amorim", "torres");


while($email[$i]) {
	
$numerorand = rand(1111111111,9999999999);			
$arrMail = explode("@",trim($email[$i]));			
$subject = $_POST['assunto'];
$bounda=md5(uniqid(rand()));	
$boundary= "------=_NextPart_".$bounda;
$boundary2= '"'.$boundary.'"';	
$iddoemail = rand(111111111111111, 999999999999999);
	
$headers = "Content-type: multipart/alternative; \n boundary=" . $boundary2 . "\r\n";
$headers  .= "MIME-Version: 1.0\r\n";
$headers .= "From: ".$nome." <".$de.">\n";
$headers .= "List-Unsubscribe: <mailto:".$email[$i]."?subject=Unsubscribe>, <http://".$do."/unsubscribe.php?mailid=".$iddoemail.">\n";

$headers2 = "Content-type: multipart/alternative; \n boundary=" . $boundary2 . "\r\n";
$headers2  .= "MIME-Version: 1.0\r\n";
$de2 = $arrX[$randIndex].$arrY[$randIndex2].rand(111, 999)."@".$_SERVER['HTTP_HOST'];
$headers2 .= "From: ".$nome." <".$de2.">\n";
$headers2 .= "List-Unsubscribe: <mailto:".$email[$i]."?subject=Unsubscribe>, <http://".$do."/unsubscribe.php?mailid=".$iddoemail.">\n";
	
	
$message .= "--" . $boundary . "\n";
$message .= "Content-type: text/plain; charset=".$iso."\n";
$message .= "Content-Transfer-Encoding: base64". "\n\n";
$message .= $texto ."\n\n";
$message .="--" . $boundary . "\n";
$message .="Content-type: text/html; charset=".$iso."\n";
$message .= "Content-Transfer-Encoding: base64". "\n\n";
$message .= $htm . "\n\n";
$message .= "--" . $boundary . "--";

$subject = str_replace('{email}',$arrMail[0],$subject);			
$subject = str_replace('{codigo}',md5(time().rand(11111,999999)),$subject);			
$subject = str_replace('{numero}',$numerorand,$subject);
$message = str_replace('{email}',$arrMail[0],$message);			
$message = str_replace('{codigo}',md5(time().rand(11111,999999)),$message);			
$message = str_replace('{numero}',$numerorand,$message);

	
$palavras = array ("@hotmail.com", "@hotmail.com.br", "@outlook.com", "@outlook.com.br", "@msn.com.br", "@msn.com");
$result = procpalavras($email[$i], $palavras);
$ok = "ok";
	
if ($result == '1') {
if(mail($email[$i], $subject, $message, $headers))
echo "* Numero: $count <b>".$email[$i]."</b> <font color=green>OK</font><br><hr>";
else
echo "* Numero: $count <b>".$email[$i]."</b> <font color=red>ERR</font><br><hr>";
$i++;
$count++;
} else {
mail($email[$i], $subject, $message, $headers2);
echo "* Numero: $count <b>".$email[$i]."</b> <font color=green>OKDK</font><br><hr>";
$i++;
$count++;
}
}
$count--;
if($ok == "ok")
echo " <font color=red>ENVIO TERMINADO</font><br><hr>";
}
?>
