-----
layout: default
saying: That makes this a happening place.
-----

# Git log cheat-sheet
because the documentation is not organized the way I want it.

## Custom formats

    git log --format="format string goes here"

where format can include these special variables:

   * hash: the whole thing is %H or abbreviated %h
   * message: The whole thing is %B; first line (aka subject) is %s and the rest (aka body) is in %b.
   * author: name (%an) and email (%ae)
   * committer: name (%cn) and email (%ce)
   * dates:
<table>
  <tr><td>Example<td></td>author</td><td>commit</td></tr>
  <tr><td>Tue Sep 3 19:36:09 2013 +0200</td><td>ad</td><td>cd</td></tr>
  <tr><td>Tue, 3 Sep 2013 19:36:09 +0200</td><td>aD</td><td>cD</td></tr>
  <tr><td>13 days ago</td><td>ar</td><td>cr</td><td>relative</td></tr>
  <tr><td>2013-09-03 19:36:09 +0200</td><td>ai</td><td>ci</td><td>sortable</td></tr>
  <tr><td>1378229769</td><td>at</td><td>ct</td><td>Unix timestamp</td></tr>
</table>
   * branches and tags: %d (like --decorate)
   * useful characters
      * newline: %n
      * percent: %%
      * hex character: %x00
   * change the colors: %Cred %Cblue %Cgreen %Creset


Weird things I haven't wanted to use yet:

   * tree fingerprint: whole hash %T or abbreviated %t
   * parent hashes: whole %P or abbreviated %p
   * encoding: %e
   * first line of commit message, except turned into a filename: %f
   * commit notes: %N
   * signed commits: %GG for message, %G? for bad/good, %GS for signer
   * reflog information: use with -g only.
      * selector: %gd for the descriptor like HEAD@{1}, or %gD for a longer version
      * identity (when is this ever not you?): name is %gn and email %ge
      * subject: how did we get here? %gs
   * boundary mark (I only see it printing greater-than): %m
   * make a newline before the field only if it has something in it: (for instance, the mssage body) %+b
   * space-delimit, so put a space before the field only if it has something in it: % field (there's a space in there)
   * if you want a newline after the last message, use tformat insteam of format.
