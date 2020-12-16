---
title: "[MS-WINERRATA]: SMB2 Remote Direct Memory Access (RDMA) Transport Protocol"
description: "This topic lists the Errata found in [MS-SMBD]    since it was last published. Since this topic is updated frequently, we    recommend that you"
---

# [MS-SMBD]: SMB2 Remote Direct Memory Access (RDMA) Transport Protocol

<p align="right"><a href="https://msdn.microsoft.com/en-us/library/ba71a9e9-4dcb-4de9-abfd-2f81d6f5f4a0">msdn link</a></p>
<p> </p>

<table>
 <thead>
  <tr>
   <th>
   <p>This topic lists the Errata found in [MS-SMBD]
   since it was last published. Since this topic is updated frequently, we
   recommend that you subscribe to these RSS or Atom feeds to receive update notifications.</p>
   <p>Errata are subject to the same terms as the
   Open Specifications documentation referenced.</p>
   </th>
   <th>
   <p><img id="Picture 59" src="MS-WINERRATA_files/image001.png"><span><a href="http://blogs.msdn.com/b/protocol_content_errata/rss.aspx">RSS</a></span>
   </p>
   <p><img id="Picture 60" src="MS-WINERRATA_files/image001.png"><span><a href="http://blogs.msdn.com/b/protocol_content_errata/atom.aspx">Atom</a></span>
   </p>
   <p> </p>
   </th>
  </tr>
 </thead>
</table>

<p>To view a PDF file of the errata for the previous versions
of this document, see the following ERRATA Archives:</p>

<p>October 16, 2015 - <span><a href="http://go.microsoft.com/fwlink/?LinkID=690377">Download</a></span></p>

<p>June 30, 2015 - <span><a href="http://go.microsoft.com/fwlink/?LinkId=617579">Download</a></span></p>

<p>Errata below are for Protocol Document Version <span><a href="https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-smbd/1ca5f4ae-e5b1-493d-b87d-f4464325e6e3">V12.0
– 2018/09/12</a></span>.</p>

<table><thead>
  <tr>
   <th>
   <p>Errata Published*</p>
   </th>
   <th>
   <p>Description</p>
   </th>
  </tr>
 </thead><tbody><tr>
  <td>
  <p>2019/11/11</p>
  </td>
  <td>
  <p>In Section 2.2.3.1, Buffer Descriptor V1
  Structure&#8203;, changed the structure name from
  SMB_DIRECT_BUFFER_DESCRIPTOR_1 to SMB_DIRECT_BUFFER_DESCRIPTOR_V1.&#8203;</p>
  <p>&#8203;</p>
  <p>Changed from:&#8203;</p>
  <p>The SMB_DIRECT_BUFFER_DESCRIPTOR_1 structure
  represents a registered RDMA buffer and is used to Advertise the source and
  destination of RDMA Read and RDMA Write operations, respectively. The upper
  layer optionally embeds one or more of these structures in its payload when
  requesting RDMA direct placement of peer data via the protocol. &#8203;</p>
  <p>...&#8203;</p>
  <p>&#8203;</p>
  <p>Changed to:&#8203;</p>
  <p>The SMB_DIRECT_BUFFER_DESCRIPTOR_V1 structure
  represents a registered RDMA buffer and is used to Advertise the source and
  destination of RDMA Read and RDMA Write operations, respectively. The upper
  layer optionally embeds one or more of these structures in its payload when
  requesting RDMA direct placement of peer data via the protocol. &#8203;</p>
  <p>...&#8203;</p>
  </td>
 </tr><tr>
  <td>
  <p>2019/11/11</p>
  </td>
  <td>
  <p>&#8203;In Section  3.1.5.1, Sending Upper Layer
  Messages, the following was changed from:&#8203;</p>
  <p>&#8203;</p>
  <p>...&#8203;</p>
  <p>&#8203;</p>
  <p>The new messages to be sent, if any, MUST be appended
  to the list of messages in the Connection.SendQueue. If there are no messages
  to be sent and Connection.SendImmediate is TRUE, a newly constructed Data
  Transfer Message MUST be added to Connection.SendQueue.&#8203;</p>
  <p>&#9679;   the credit processing specified in section
  3.1.5.9 MUST be performed, and the CreditsGranted field of the first message
  in Connection.SendQueue MUST be incremented by the number of new credits
  returned. &#8203;</p>
  <p>For each message in Connection.SendQueue:&#8203;</p>
  <p>&#9679;   If Connection.SendCredits is 0, stop
  processing messages, and break the loop.&#8203;</p>
  <p>&#9679;   If Connection.SendCredits is 1 and the
  CreditsGranted field of the message is 0, then at least one credit MUST be
  granted to the peer to prevent deadlock. If the processing specified in
  section 3.1.5.9 returns zero, stop processing Sends, and break the loop.
  Otherwise, increment the CreditsGranted field of the current first message in
  Connection.SendQueue by the number of new credits returned.&#8203;</p>
  <p>&#9679;   The first message MUST be removed from
  Connection.SendQueue.&#8203;</p>
  <p>&#9679;   The value of Connection.SendCredits MUST be
  decremented by one.&#8203;</p>
  <p>&#9679;   The value of the CreditsRequested field of
  the message MUST be set to Connection.SendCreditTarget.&#8203;</p>
  <p>&#9679;   If Connection.KeepaliveRequested is
  &quot;PENDING&quot;, the Flags field of the message MUST be set to
  SMB_DIRECT_RESPONSE_REQUESTED, Connection.KeepaliveRequested MUST be set to
  &quot;SENT&quot;, and the Idle Connection Timer SHOULD&lt;3&gt; be set to an
  implementation-specific value. Otherwise, the Flags field of the message MUST
  be set to 0x0000.&#8203;</p>
  <p>&#9679;   If the message to be sent was provided with
  an optional remote memory token to be invalidated on the receiving peer, the
  token SHOULD be provided in an implementation-specific manner to the RDMA
  provider when sending. If sending of remote invalidation is not supported by
  the RDMA provider, the token MAY be ignored.&#8203;</p>
  <p>&#9679;   The message MUST be sent on the connection
  in an implementation-specific manner, and any error MUST be returned to the
  caller.&#8203;</p>
  <p>&#9679;   If Connection.SendQueue is empty,
  Connection.SendImmediate MUST be set to FALSE and success MUST be returned to
  the caller.&#8203;</p>
  <p>&#8203;</p>
  <p>Changed to:&#8203;</p>
  <p>&#8203;</p>
  <p>...&#8203;</p>
  <p>&#8203;</p>
  <p>For each message in Connection.SendQueue:&#8203;</p>
  <p>&#9679;   If Connection.SendCredits is 0, stop
  processing.&#8203;</p>
  <p>&#9679;   If CreditsGranted field of the first message
  in Connection.SendQueue is zero, the credit processing specified in section
  3.1.5.9 MUST be performed, and the CreditsGranted field of the message MUST
  be set to the number of new credits returned. &#8203;</p>
  <p>&#9679;   If Connection.SendCredits is 1 and the
  CreditsGranted field of the message is 0, stop processing.&#8203;</p>
  <p>&#9679;   The first message MUST be removed from
  Connection.SendQueue.&#8203;</p>
  <p>&#9679;   The value of Connection.SendCredits MUST be
  decremented by one.&#8203;</p>
  <p>&#9679;   The value of the CreditsRequested field of
  the message MUST be set to Connection.SendCreditTarget.&#8203;</p>
  <p>&#9679;   If Connection.KeepaliveRequested is
  &quot;PENDING&quot;, the Flags field of the message MUST be set to
  SMB_DIRECT_RESPONSE_REQUESTED, Connection.KeepaliveRequested MUST be set to
  &quot;SENT&quot;, and the Idle Connection Timer SHOULD&lt;3&gt; be set to an
  implementation-specific value. Otherwise, the Flags field of the message MUST
  be set to 0x0000.&#8203;</p>
  <p>&#9679;   If the message to be sent was provided with
  an optional remote memory token to be invalidated on the receiving peer, the
  token SHOULD be provided in an implementation-specific manner to the RDMA
  provider when sending. If sending of remote invalidation is not supported by
  the RDMA provider, the token MAY be ignored.&#8203;</p>
  <p>&#9679;   The message MUST be sent on the connection
  in an implementation-specific manner.&#8203;</p>
  <p>&#9679;   Connection.SendImmediate MUST be set to
  FALSE. &#8203;</p>
  <p>&#8203;</p>
  <p>In Section 3.1.5.8, Receiving a Data Transfer Message,
  the following was changed from:&#8203;</p>
  <p>&#8203;</p>
  <p>...&#8203;</p>
  <p>&#8203;</p>
  <p>If Connection.SendQueue is empty, the credit
  processing specified in section 3.1.5.9 MUST be performed. If the number of
  new credits returned is greater than zero, the receiver MUST set
  Connection.SendImmediate to TRUE and MUST promptly send a Data Transfer message
  on the Connection, as specified in section 3.1.5.1. &#8203;</p>
  <p>&#8203;</p>
  <p>...&#8203;</p>
  <p>&#8203;</p>
  <p>Changed to:&#8203;</p>
  <p>&#8203;</p>
  <p>...&#8203;</p>
  <p>If Connection.SendQueue is empty, the credit
  processing specified in section 3.1.5.9 MUST be performed. If the number of
  new credits returned is greater than zero, the receiver MUST promptly send a
  newly constructed Data Transfer message with its CreditsGranted field set to
  the number of new credits on the Connection, as specified in section 3.1.5.1.
  &#8203;</p>
  <p>...&#8203;</p>
  </td>
 </tr></tbody></table>

<p>*Date format: YYYY/MM/DD</p>


                