# fileInputにBootstrapを当てる

```html
<style type="text/css">
.btn-file {
  position: relative;
  overflow: hidden;
}
.btn-file input[type=file] {
  position: absolute;
  top: 0;
  right: 0;
  min-width: 100%;
  min-height: 100%;
  font-size: 100px;
  text-align: right;
  filter: alpha(opacity=0);
  opacity: 0;
  background: red;
  cursor: inherit;
  display: block;
}
input[readonly] {
  background-color: white !important;
  cursor: text !important;
}
</style>

<script type="text/javascript">
$(document).on('change', '.btn-file :file', function() {
  var input = $(this),
  numFiles = input.get(0).files ? input.get(0).files.length : 1,
  label = input.val().replace(/\\/g, '/').replace(/.*\//, '');
  input.trigger('fileselect', [numFiles, label]);
});
$(document).ready( function() {
  $('.btn-file :file').on('fileselect', function(event, numFiles, label) {
    var input = $(this).parents('.input-group').find(':text'),
    log = numFiles > 1 ? numFiles + ' files selected' : label;
    if( input.length ) {
      input.val(log);
    } else {
      if( log ) alert(log);
    }
  });
});
</script>

<div class="select_file">
  <div class="input-group">
    <span class="input-group-btn">
      <span class="btn btn-primary btn-file form-control">
        ファイルを選択{{form.file}}
      </span>
    </span>
    <input type="text" class="form-control" readonly="readonly">
  </div>
</div>
```
