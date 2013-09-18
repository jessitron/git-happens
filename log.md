---
layout: default
saying: That makes this a happening place.
---

# Git log cheat-sheet
because the documentation is not organized the way I want it.

## Custom formats

    git log --format="format string goes here"

where format can include these special variables:

* __hash__ : the whole thing is %H or abbreviated %h
* __message__: The whole thing is %B; first line (aka subject) is %s and the rest (aka body) is in %b.
* __author__: name (%an) and email (%ae)
* __committer__: name (%cn) and email (%ce)
* __dates__:

<table>
  <tr>
    <td>Example<td></td>author</td><td>commit</td>
  </tr>
  <tr>
    <td>Tue Sep 3 19:36:09 2013 +0200</td><td>ad</td><td>cd</td>
  </tr>
  <tr>
    <td>Tue, 3 Sep 2013 19:36:09 +0200</td><td>aD</td><td>cD</td>
  </tr>
  <tr>
    <td>13 days ago</td><td>ar</td><td>cr</td><td>relative</td>
  </tr>
  <tr>
    <td>2013-09-03 19:36:09 +0200</td><td>ai</td><td>ci</td><td>sortable</td>
  </tr>
  <tr>
    <td>1378229769</td><td>at</td><td>ct</td><td>Unix timestamp</td>
  </tr>
</table>

* __branches and tags__: %d (like --decorate)
* useful characters
  * __newline__: %n
  * __percent__: %%
  * __hex character__: %x00
* __change the colors__: %Cred %Cblue %Cgreen %Creset


Weird things I haven't wanted to use yet:

* __tree fingerprint__: whole hash %T or abbreviated %t
* __parent hashes__: whole %P or abbreviated %p
* __encoding__: %e
* first line of commit message, except turned into a filename: %f
* __commit notes__: %N
* __signed commits__: %GG for message, %G? for bad/good, %GS for signer
* __reflog information__: use with -g only.
  * __selector__: %gd for the descriptor like HEAD@{1}, or %gD for a longer version
  * __identity__ (when is this ever not you?): name is %gn and email %ge
  * __subject__: how did we get here? %gs
* boundary mark (I only see it printing greater-than): %m
* make a newline before the field only if it has something in it: (for instance, the mssage body) %+b
* space-delimit, so put a space before the field only if it has something in it: % field (there's a space in there)
* if you want a newline after the last message, use tformat insteam of format.
