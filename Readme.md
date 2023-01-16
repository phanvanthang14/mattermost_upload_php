## Upload file mattermost using curl php

$curl = curl_init();

curl_setopt_array($curl, array(
    CURLOPT_URL => config('schat.url')."/api/v4/files",
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_TIMEOUT => 0,
    CURLOPT_FOLLOWLOCATION => false,
    CURLOPT_CUSTOMREQUEST => "POST",
    CURLOPT_POSTFIELDS => array('files' => curl_file_create($path), 'channel_id' => $channel['id']),
    CURLOPT_HTTPHEADER => array(
        "Authorization: Bearer ". config('schat.token'),
        "Content-Type: multipart/form-data"
    ),
));
$response = json_decode(curl_exec($curl), true);

## Send file to channel

post = json_decode('{"message": "message", "channel_id": "' . $channel['id'] . '", "file_ids": ["'.$response['file_infos'][0]['id'].'"]}', true);
