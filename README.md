# projekrizky
Tugas UTS PWF
<?php
    $servername = "localhost";
    $username = "root";
    $password = "";
    $databasename = "membuatapi";

    $conn = mysqli_connect($servername, $username, $password, $databasename);
    if(!$conn){
    	die("Koneksi tidak berhasil");

    }
 
<?php
    //Koneksi ke database mysql
    include "conn.php";

    //Membuat query/sql untuk mengambil seluruh data pegawai
    $sql = "SELECT * FROM siswa";
    $query = mysqli_query($conn, $sql);
    while($data = mysqli_fetch_array($query)){
	    //echo $data["nama_siswa"]." ";

	    $item[] = array(
            'nama'=>$data["nama_siswa"],
            'NIK' =>$data["NIK"],
            'alamat' =>$data["alamat"],
            'id' =>$data["id_siswa"]
        );
    }

    $response = array (
        'status'=>'OK',
        'data'=>$item
    );

    echo json_encode($response);
    
?>
 
