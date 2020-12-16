---
title: "[MS-WINERRATA]: Microsoft NT Backup File Structure"
description: "This topic lists the Errata found in the MS-BKUP    document since it was last published. Since this topic is updated    frequently, we recommend"
---

# [MS-BKUP]: Microsoft NT Backup File Structure

<p align="right"><a href="https://msdn.microsoft.com/en-us/library/eb869ede-eea7-4358-b489-daaca74eb1e9">msdn link</a></p>
<p> </p>

<table>
 <thead>
  <tr>
   <th>
   <p>This topic lists the Errata found in the MS-BKUP
   document since it was last published. Since this topic is updated
   frequently, we recommend that you subscribe to these RSS or Atom feeds to
   receive update notifications.</p>
   <p>Errata are subject to the same terms as the
   Open Specifications documentation referenced.</p>
   </th>
   <th>
   <p><img id="Picture 362" src="MS-WINERRATA_files/image002.png"><span><a href="http://blogs.msdn.com/b/protocol_content_errata/rss.aspx">RSS</a></span>
   </p>
   <p><img id="Picture 357" src="MS-WINERRATA_files/image002.png"><span><a href="http://blogs.msdn.com/b/protocol_content_errata/atom.aspx">Atom</a></span>
   </p>
   <p> </p>
   </th>
  </tr>
 </thead>
</table>

<p>Errata below are for Protocol Document Version <span><a href="https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-bkup/f67950c8-d583-469a-83dd-c4ff4cedf533">V9.0
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
  <p>2020/04/27</p>
  </td>
  <td>
  <p>In Section 2.13.1, Creating an NT Backup File, a new
  paragraph was added to the end of the section.</p>
  <p> </p>
  <p>Added:</p>
  <p> </p>
  <p>If F has any ghosted extents, the NT backup file MUST
  generate one GHOSTED_EXTENT backup stream structure. During restore the
  GHOSTED_EXTENT backup stream structure is presented to the filesystem to
  recreate the file ghosted extent state.</p>
  <p> </p>
  <p>The following new sections were added:</p>
  <p> </p>
  <p>2.12   FileSystem Ghosted Extents Functionality</p>
  <p> </p>
  <p>Hierarchical Storage Management (HSM) solutions on top
  of a filesystem remove cold data and move it to the next storage tier. This
  movement creates sparse holes in file system data, and HSM solutions have to
  maintain mappings between those sparse holes and location of the data in the
  new tier. An implementation of the Ghosted extents feature helps this process
  by maintaining some token in the sparse holes, on behalf of the HSM solution.
  This obviates the need for the HSM solution to maintain its own mappings.
  When a file with such tokens, hereby referred to as ghosted extents, are
  backed up, the backup process should store the tokens and their locations in
  the backup stream state. On restore those tokens should be reinserted in the
  data stream in exactly the same locations to recreate the original file
  state. The method to query the tokens, serialize the tokens, and restore the
  tokens is file system implementation specific.</p>
  <p> </p>
  <p>2.12.1   Ghosted Extents Stream Structure</p>
  <p> </p>
  <p>A ghosted extent stream structure represents ghosted
  extents in the DATA backup stream. Ghosted extents are a kind of sparse
  extents, which store a GUID representing the owner of the extent and some
  variable-sized metadata. The structure of the data portion of this backup
  stream for a specific implementation is as follows:</p>
  <p> </p>
  <p>0   1   2   3   4   5   6   7   8   9   1</p>
  <p> </p>
  <p>0   1   2   3   4   5   6   7   8   9   2</p>
  <p> </p>
  <p>0   1   2   3   4   5   6   7   8   9   3</p>
  <p> </p>
  <p>0   1</p>
  <p> </p>
  <p>Count</p>
  <p> </p>
  <p>TotalCount</p>
  <p> </p>
  <p>Data (variable)</p>
  <p> </p>
  <p>...</p>
  <p> </p>
  <p>Count (4 bytes): The number of extents in the Data
  portion.</p>
  <p> </p>
  <p>TotalCount (4 bytes): The total number of ghosted
  extents in the stream.</p>
  <p> </p>
  <p>Data (Variable):  The data portion of the above
  structure contains a variable number of extents. The number of extents is
  given by Count. The structure of each Extent is described below:</p>
  <p> </p>
  <p>0   1   2   3   4   5   6   7   8   9   1</p>
  <p> </p>
  <p>0   1   2   3   4   5   6   7   8   9   2</p>
  <p> </p>
  <p>0   1   2   3   4   5   6   7   8   9   3</p>
  <p> </p>
  <p>0   1</p>
  <p> </p>
  <p>Offset</p>
  <p> </p>
  <p>...</p>
  <p> </p>
  <p>Length</p>
  <p> </p>
  <p>...</p>
  <p> </p>
  <p>Guid</p>
  <p> </p>
  <p>...</p>
  <p> </p>
  <p>...</p>
  <p> </p>
  <p>...</p>
  <p> </p>
  <p>NextOffset</p>
  <p> </p>
  <p>Size</p>
  <p> </p>
  <p>Data (variable)</p>
  <p> </p>
  <p>...</p>
  <p> </p>
  <p>Offset (8 bytes): The logical byte offset in the DATA
  backup stream where the ghosted extent starts.</p>
  <p> </p>
  <p>Length (8 bytes): The logical length of the ghosted
  extent.</p>
  <p> </p>
  <p>GUID (16 bytes): The GUID identifier of the owner for
  the ghosted extent.</p>
  <p> </p>
  <p>NextOffset (4 bytes): Offset to the next Extent structure.</p>
  <p> </p>
  <p>Size (4 bytes): Size of the metadata of the ghosted
  extent.</p>
  <p> </p>
  <p>Data (variable): Metadata of the ghosted extent.</p>
  </td>
 </tr><tr>
  <td></td>
  <td>
  <p> </p>
  </td>
 </tr></tbody></table>

<p>*Date format: YYYY/MM/DD</p>


                