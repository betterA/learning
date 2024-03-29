## UDP 还是 TCP？

如果抛开 WebRTC，让你自己实现一套**实时互动**直播系统，在选择网络传输协议时，你会选择使用**UDP**协议还是**TCP**协议呢？

这个问题在 2011 年至 2012 年一直是一件困扰着我们整个团队的大事儿，因为当时在国内很少有用 UDP 作为底层传输协议的。UDP 虽然传输快，但不可靠，尤其是在用户的网络质量很差的情况下，基本无法保障音视频的服务质量。

当时能想到的解决方案是，如果采用 UDP 作为底层传输协议，那就使用 RUDP（可靠性 UDP），只有这样才能保障传输过程中不丢包。但有人提出反对意见，认为如果想不丢包，就该使用 TCP，因为 RUDP 可靠性做到极致就变成 TCP 了，那为什么不直接使用 TCP 呢？

面对这种情况，2019 年的你会做何种选择呢？UDP 还是 TCP？你能拿出让人真正信服的理由吗？

