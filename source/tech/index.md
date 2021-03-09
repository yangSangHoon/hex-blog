---
title: RTCPeerConnection을 이용한 sdp, candidate 교환 및 협상
layout: 'tech'
---

## 두 peer간 협상 과정 예시

한쪽 입장에서 caller와 callee로 두 유저를 정한 동선
(peer를 교환할 수 있는 signaling서버가 필요)
1. caller가 createOffer메서드를 통하여 sdp생성, setLocalDescription(sdp) 해당 전문 로컬에 셋팅 후 callee에게 전달
2. callee는 setRemoteDescription로 받은 전문 저장, createAnswer로 응답 sdp생성, setLocalDescription로 본인 전문 저장 후 caller에게 전달
3. 두 peer는 각각 onicecandiate이벤트로 생성한 candidate를 서로에게 전달 addIceCandidate(e.candidate)로 상대의 후보자 정보(network정보)를 등록
4. ontrack으로 상대방의 stream을 받아 play

