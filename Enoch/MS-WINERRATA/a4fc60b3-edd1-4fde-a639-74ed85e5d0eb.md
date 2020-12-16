---
title: "[MS-WINERRATA]: Enhanced Metafile Format Plus Extensions"
description: "This topic lists the Errata found in the MS-EMFPLUS    document since it was last published. Since this topic is updated    frequently, we"
---

# [MS-EMFPLUS]: Enhanced Metafile Format Plus Extensions

<p align="right"><a href="https://msdn.microsoft.com/en-us/library/a4fc60b3-edd1-4fde-a639-74ed85e5d0eb">msdn link</a></p>
<p> </p>

<table>
 <thead>
  <tr>
   <th>
   <p>This topic lists the Errata found in the MS-EMFPLUS
   document since it was last published. Since this topic is updated
   frequently, we recommend that you subscribe to these RSS or Atom feeds to
   receive update notifications.</p>
   <p>Errata are subject to the same terms as the
   Open Specifications documentation referenced.</p>
   <p> </p>
   </th>
   <th>
   <p><img id="Picture 143" src="MS-WINERRATA_files/image001.png"><span><a href="http://blogs.msdn.com/b/protocol_content_errata/rss.aspx">RSS</a></span>
   </p>
   <p><img id="Picture 142" src="MS-WINERRATA_files/image001.png"><span><a href="http://blogs.msdn.com/b/protocol_content_errata/atom.aspx">Atom</a></span>
   </p>
   <p> </p>
   </th>
  </tr>
 </thead>
</table>

<p>To view a PDF file of the errata for the previous versions
of this document, see the following ERRATA Archives:</p>

<p>October 16, 2015 - <span><a href="http://go.microsoft.com/fwlink/?LinkID=690377">Download</a></span></p>

<p>June 30, 2015 - <span><a href="http://go.microsoft.com/fwlink/?LinkId=617579">Download</a></span> </p>

<p>March 4, 2020 - <span><a href="https://winprotocoldoc.blob.core.windows.net/productionwindowsarchives/MS-WINERRATA/%5bMS-WINERRATA%5d-200304.pdf">Download</a></span></p>

<p>Errata below are for Protocol Document Version <span><a href="https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-emfplus/5f92c789-64f2-46b5-9ed4-15a9bb0946c6">V17.0
– 2020/03/04</a></span>.</p>

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
  <p>2020/07/06</p>
  </td>
  <td>
  <p>In Section 2.2.3.4, ColorCurveEffect Object, added
  midtone adjustment range to AdjustmentIntensity field.</p>
  <p> </p>
  <p>Changed from:</p>
  <p> </p>
  <p>Shadow adjustment range:</p>
  <table><thead>
    <tr>
     <th>
     <p>Value</p>
     </th>
     <th>
     <p>Meaning</p>
     </th>
    </tr>
   </thead><tbody><tr>
    <td>
    <p>-100 &#8804; value &lt; 0</p>
    </td>
    <td>
    <p>As the value decreases, the dark areas of the image 
    SHOULD appear darker.</p>
    </td>
   </tr><tr>
    <td>
    <p>0</p>
    </td>
    <td>
    <p>A value of 0 specifies that the shadow MUST NOT 
    change.</p>
    </td>
   </tr><tr>
    <td>
    <p>0 &lt; value &#8804; 100</p>
    </td>
    <td>
    <p>As the value increases, the dark areas of the image 
    SHOULD appear lighter.</p>
    </td>
   </tr></tbody></table>
  <p> </p>
  <p> </p>
  <p>Changed to:</p>
  <p> </p>
  <p>Shadow adjustment range:</p>
  <table><thead>
    <tr>
     <th>
     <p>Value</p>
     </th>
     <th>
     <p>Meaning</p>
     </th>
    </tr>
   </thead><tbody><tr>
    <td>
    <p>-100 &#8804; value &lt; 0</p>
    </td>
    <td>
    <p>As the value decreases, the dark areas of the image 
    SHOULD appear darker.</p>
    </td>
   </tr><tr>
    <td>
    <p>0</p>
    </td>
    <td>
    <p>A value of 0 specifies that the shadow MUST NOT 
    change.</p>
    </td>
   </tr><tr>
    <td>
    <p>0 &lt; value &#8804; 100</p>
    </td>
    <td>
    <p>As the value increases, the dark areas of the image 
    SHOULD appear lighter.</p>
    </td>
   </tr></tbody></table>
  <p>Midtone adjustment range:</p>
  <table><thead>
    <tr>
     <th>
     <p>Value</p>
     </th>
     <th>
     <p>Meaning</p>
     </th>
    </tr>
   </thead><tbody><tr>
    <td>
    <p>-100 &#8804; value &lt; 0</p>
    </td>
    <td>
    <p>As the value decreases, the midtones of the image 
    SHOULD appear darker.</p>
    </td>
   </tr><tr>
    <td>
    <p>0</p>
    </td>
    <td>
    <p>A value of 0 specifies that the midtone MUST NOT 
    change.</p>
    </td>
   </tr><tr>
    <td>
    <p>0 &lt; value &#8804; 100</p>
    </td>
    <td>
    <p>As the value increases, the midtones of the image 
    SHOULD appear lighter.</p>
    </td>
   </tr></tbody></table>
  <p>
  </td>
 </tr></tbody></table>

<p>*Date format: YYYY/MM/DD</p>


                