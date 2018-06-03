<template>
  <!--<div class="panel panel_is_show">
              <div class="panel_content">
                  <div class="panel_title">您确认删除这个商品吗？</div>
                  <div class="panel_footer">
                      <button class="cancel">取消</button>
                      <button class="submit">确定</button>
                  </div>
              </div>
          </div>-->

  <div class="modal fade" tabindex="-1" role="dialog" id="myModal">
    <div class="modal-dialog " role="document">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
          <h4 class="modal-title"></h4>
        </div>
        <div class="modal-body">
          <p>您确认删除这个商品吗？</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">取消</button>
          <button type="button" class="btn btn-info" @click="deleteShop()" data-dismiss="modal">确定</button>
        </div>
      </div><!-- /.modal-content -->
    </div><!-- /.modal-dialog -->
  </div><!-- /.modal -->
</template>

<script>
  export default {

  }
</script>

<style>

</style>
