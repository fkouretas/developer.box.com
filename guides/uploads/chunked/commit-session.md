---
rank: 3
related_endpoints:
  - post_files_upload_sessions_id_commit
related_guides: []
related_pages: []
required_guides:
  - uploads/chunked/create-session
  - uploads/chunked/upload-part
related_resources:
  - upload_session
  - upload_part
alias_paths: []
category_id: uploads
subcategory_id: uploads/chunked
is_index: false
id: uploads/chunked/commit-session
type: guide
total_steps: 5
sibling_id: uploads/chunked
parent_id: uploads/chunked
next_page_id: uploads/chunked/folder
previous_page_id: uploads/chunked/create-session
source_url: >-
  https://github.com/box/developer.box.com/blob/master/content/guides/uploads/chunked/commit-session.md
---

# Commit Upload Session

The final step in a chunked upload is to commit the session.

To commit a file upload session, call the
[`POST /files/upload_sessions/:id/commit`][e_commit] with a list of uploaded
parts to commit.

<Samples id='post_files_upload_sessions_id_commit' >

</Samples>

<Message>

Additionally, any file `attributes` can be passed along with the `parts` to
further add information to the file. See the [`POST /files/content`][e_file]
API for more details.

</Message>

## Response

When successful, the API returns a HTTP `201 Created` status code with a
[`File`][r_file] object.

In some cases, creating the parts might not be ready yet and the API will return
a `202 Accepted` status code instead. In this case the application should check
the `Retry-After` header and retry committing after the number of seconds
specified.

[e_commit]: e://post_files_upload_sessions_id_commit
[e_file]: e://post_files_content
[r_file]: r://file