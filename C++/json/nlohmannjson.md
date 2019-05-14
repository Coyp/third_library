https://github.com/nlohmann/json  

```c++
json singleTaskJson;
singleTaskJson["taskId"] = task_config_.get_task_id();
singleTaskJson["inputUrl"] = task_config_.get_input_url()[task_config_.get_current_media_index()];
json videoJson;
videoJson["mediaType"] = std::string("video");
videoJson["byteRate"] = videoStats.byte_rate;
videoJson["packetsLostRate"] = videoStats.packet_lost_rate;
json audioJson;
audioJson["mediaType"] = std::string("audio");
audioJson["byteRate"] = audioStats.byte_rate;
audioJson["packetsLostRate"] = audioStats.packet_lost_rate;
singleTaskJson["peerStats"].push_back(videoJson);
singleTaskJson["peerStats"].push_back(audioJson);

singleTaskJson.dump();
```
