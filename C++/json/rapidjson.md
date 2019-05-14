https://github.com/Tencent/rapidjson  

```c++
Value value;
Document jsonDoc;
Pointer("/peerId").Set(jsonDoc, peer_id.c_str());
Pointer("/peerStats/0/mediaType").Set(jsonDoc, "video");
Pointer("/peerStats/0/mimeType").Set(jsonDoc, video_stats.mime_type.c_str());
value.SetDouble(video_stats.byte_rate);
Pointer("/peerStats/0/byteRate").Set(jsonDoc, value);
value.SetDouble(video_stats.packet_lost_rate);
Pointer("/peerStats/0/packetsLostRate").Set(jsonDoc, value);
Pointer("/peerStats/1/mediaType").Set(jsonDoc, "audio");
Pointer("/peerStats/1/mimeType").Set(jsonDoc, audio_stats.mime_type.c_str());
value.SetDouble(audio_stats.byte_rate);
Pointer("/peerStats/1/byteRate").Set(jsonDoc, value);
value.SetDouble(audio_stats.packet_lost_rate);
Pointer("/peerStats/1/packetsLostRate").Set(jsonDoc, value);

// json转换为string
StringBuffer buffer;
Writer<StringBuffer> writer(buffer);
jsonDoc.Accept(writer);
string str = buffer.GetString();
```
