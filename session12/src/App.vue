<script setup>
import {reactive,ref,toRaw,computed} from'vue'
const activateForm=ref(false);
const checkStatusForm=ref('add');
const books=reactive(JSON.parse(localStorage.getItem('books'))||[])
const initialBook=reactive({id:0,name:'',nameUser:'',dateA:'',dateB:'',status:true})
const initialError=reactive({name:'',nameUser:'',dateA:'',dateB:''})
const deleteModal=ref(false);
const deleteBook=ref();
const searchQuery=ref('');
const resetError=()=>{
  initialError.name='';
  initialError.nameUser='';
  initialError.dateA='';
  initialError.dateB='';
}
const resetBook=()=>{
  initialBook.id=0;
  initialBook.name='';
  initialBook.nameUser='';
  initialBook.dateA='';
  initialBook.dateB='';
}
function validateDate(selectedDate) {
  const currentDate = new Date(); 
  const chosenDate = new Date(selectedDate);
  if (chosenDate <= currentDate) {
    return false;
  }
  return true; 
}
const validateBooks=()=>{
  if(initialBook.name==''){
    initialBook.name='tên sách không đc để trống';
  }
  if(initialBook.nameUser==''){
    initialBook.nameUser='tên người mượn không đc để trống';
  }
  if(initialBook.dateA==''){
    initialError.dateA='ngày mượn không đc để trống'
  }else if(!validateDate(initialBook.dateA)){
    initialError.dateA='ngày mượn  phải lớn hơn hoặc bằng ngày hiện tại'
  }
   if(initialBook.dateB==''){
    initialError.dateB='ngày trả không đc để trống'
  }else if(!validateDate(initialBook.dateB)){
    initialError.dateB='ngày trả  phải lớn hơn hoặc bằng ngày hiện tại'
  }
}
const handleSubmit=()=>{
  resetError();
  validateBooks();
  if(!initialError.name &&!initialError.nameUser&&!initialError.dateA&&initialError.dateB){
    if(checkStatusForm.value=='add'){
      initialBook.id=Math.ceil(Math.random()*100001);
      books.push({...initialBook});
    }else if(checkStatusForm.value=='edit'){
      let findNumber=books.findIndex((item)=>{
        return item.id===initialBook.id;
      })
      books.splice(findNumber,1,{...initialBook});
      checkStatusForm.value=='add';
    }
    activateForm.value=false;
    resetBook();
    localStorage.setItem("books",JSON.stringify(books));
  }
}
const blockBook=(item)=>{
  item.status=!item.status;
  localStorage.setItem("books",JSON.stringify(books));
}
const handleUpdateBook=(item)=>{
  const copiedItem = {...item}
  initialBook.id=copiedItem.id;
  initialBook.name=copiedItem.name;
  initialBook.dateA=copiedItem.dateA;
  initialBook.dateB=copiedItem.dateB;
  initialBook.nameUser=copiedItem.nameUser;
  activateForm.value=true;
  checkStatusForm.value='edit';
}
const handleDeleteModal=(item)=>{
  deleteModal.value=true;
  deleteBook.value=item;
}
const handleDelete=()=>{
      let findNumber=books.findIndex((item)=>{
        return item.id===deleteBook.id;
      })
      books.splice(findNumber,1);
       localStorage.setItem("books",JSON.stringify(books));
       deleteModal.value=false;
}
const handleCloseDelete=()=>{
  deleteModal.value=false;
}
const filterBooks = computed(() => {
  if (searchQuery.value) {
    return books.filter((item)=>{ 
      return item.name.toLowerCase().includes(searchQuery.value.toLowerCase());
    })
  }
  return books;
});
const addUser=()=>{
  activateForm.value=true;
}
const handleCloseForm=()=>{
  activateForm.value=false;
}
</script>
<template>
 <body>
    <div class="w-[80%] m-auto mt-4 h-[100vh]">
      <main class="main">
        <header class="d-flex justify-content-between mb-3">
          <h3>Nhân viên</h3>
          <button class="btn btn-primary" @click='addUser'>Thêm mới nhân viên</button>
        </header>
        <div class="d-flex align-items-center justify-content-end gap-2 mb-3">
          <input
            style="width: 350px"
            type="text"
            class="form-control"
            placeholder="Tìm kiếm theo email"
            v-model="searchQuery"
          />
          <i  class="fa-solid fa-arrows-rotate" title="Refresh"></i>
        </div>
        <table class="table table-bordered table-hover table-striped">
          <thead>
            <tr>
              <th>STT</th>
              <th>Tên sách </th>
              <th>Người mượn</th>
              <th>Ngày mượn </th>
              <th>Ngày trả</th>
              <th>Trạng thái</th>
              <th colspan="2">Chức năng</th>
            </tr>
          </thead>
          <tbody>
            <tr :key='item.id' v-for="item in filterBooks">
              <td>{{item.id}}</td>
              <td>{{item.name}}</td>
              <td>{{item.nameUser}}</td>
              <td>{{item.dateA}}</td>
              <td>{{item.dateB}}</td>
              <td>
                <div style="display: flex; align-items: center; gap: 8px">
                  <div class="status status-active"></div>
                  <span>{{item.status?'chưa trả':'đã trả'}}</span>
                </div>
              </td>
              <td>
                <span class="button button-block" @click="blockBook(item)">{{item.status?'Chặn':'Bỏ chặn'}}</span>
              </td>
              <td>
                <span class="button button-edit" @click="handleUpdateBook(item)">Sửa</span>
              </td>
              <td><span class="button button-delete" @click="handleDeleteModal(item)">Xóa</span></td>
            </tr>
          </tbody>
        </table>
        <footer class="d-flex justify-content-end align-items-center gap-3">
          <select class="form-select">
            <option selected>Hiển thị 10 bản ghi trên trang</option>
            <option>Hiển thị 20 bản ghi trên trang</option>
            <option>Hiển thị 50 bản ghi trên trang</option>
            <option>Hiển thị 100 bản ghi trên trang</option>
          </select>
          <ul class="pagination">
            <li class="page-item">
              <a class="page-link" href="#">Previous</a>
            </li>
            <li class="page-item"><a class="page-link" href="#">1</a></li>
            <li class="page-item"><a class="page-link" href="#">2</a></li>
            <li class="page-item"><a class="page-link" href="#">3</a></li>
            <li class="page-item"><a class="page-link" href="#">Next</a></li>
          </ul>
        </footer>
      </main>
    </div>
    <div v-if="activateForm" class="overlay" >
      <form class="form">
        <div class="d-flex justify-content-between align-items-center">
          <h4>{{checkStatusForm=='add'?'Thêm mới sách':'Chỉnh sửa sách'}}</h4>
          <i class="fa-solid fa-xmark" @click='handleCloseForm'></i>
        </div>
        <div>
          <label class="form-label" for="userName">Tên sách</label>
          <input  v-model="initialBook.name" id="userName" type="text" class="form-control"  />
          <div class="form-text error" v-if="initialError.name!=''">{{initialError.name}}</div>
        </div>
        <div>
          <label class="form-label" for="dateOfBirth">Tên nguoi mươn</label>
          <input  v-model="initialBook.nameUser" id="dateOfBirth"  type="text" class="form-control" />
        </div>
        <div class="form-text error" v-if="initialError.nameUser!=''" >{{initialError.nameUser}}</div>
        <div>
          <label  class="form-label" for="email">Ngày mượn</label>
          <input  v-model="initialBook.dateA" id="email" type="date" class="form-control" />
        </div>
        <div class="form-text error" v-if="initialError.dateA!=''" >{{initialError.dateA}}</div>
        <div>
          <label class="form-label" for="address">Ngày trả</label>
          <input  v-model="initialBook.dateB" id="email" type="date" class="form-control" />
        </div>
        <div>
          <button class="w-100 btn btn-primary" @click.prevent="handleSubmit">Thêm mới</button>
        </div>
      </form>
    </div>
    <!-- Modal xác nhận chặn tài khoản -->
    <div class="overlay" hidden>
      <div class="modal-custom">
        <div class="modal-title">
          <h4>Cảnh báo</h4>
          <i class="fa-solid fa-xmark"></i>
        </div>
        <div class="modal-body-custom">
          <span>Bạn có chắc chắn muốn chặn tài khoản này?</span>
        </div>
        <div class="modal-footer-custom">
          <button class="btn btn-light">Hủy</button>
          <button class="btn btn-danger">Xác nhận</button>
        </div>
      </div>
    </div>

    <!-- Modal xác nhận xóa tài khoản -->
    <div class="overlay" v-if="deleteModal">
      <div class="modal-custom">
        <div class="modal-title">
          <h4>Cảnh báo</h4>
          <i class="fa-solid fa-xmark"></i>
        </div>
        <div class="modal-body-custom">
          <span>Bạn có chắc chắn muốn xóa tài khoản này?</span>
        </div>
        <div class="modal-footer-custom">
          <button class="btn btn-light" @click="handleCloseDelete">Hủy</button>
          <button class="btn btn-danger" @click="handleDelete()">Xác nhận</button>
        </div>
      </div>
    </div>
  </body>

</template>
<style scoped>
</style>