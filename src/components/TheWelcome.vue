







.swiper{
  width: 950px;
}

.card {
  position: relative;
  background: #fff;
  border-radius: 20px;
  margin: 20px 0;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
}

.card::before{
  content: "";
  position: absolute;
  height: 40%;
  width: 100%;
  background: #7d2ae8;
  border-radius: 20px 20px 0 0;
}

 .card-content{
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 30px;
  position: relative;
  z-index: 100;
}

 .card-content .image{
  height: 140px;
  width: 140px;
  border-radius: 50%;
  padding: 3px;
  background: #7d2ae8;
}

 .card-content .image img{
  height: 100%;
  width: 100%;
  object-fit: cover;
  border-radius: 50%;
  border: 3px solid #fff;
}






.card .name-profession{
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 10px;
  
} 

.name-profession .name{
  font-size: 20px;
  font-weight: 600;
}

.name-profession .profession{
  font-size:15px;
  font-weight: 500;
}

.card-content .rating{
  display: flex;
  align-items: center;
  margin-top: 18px;
}

.card-content .rating i{
  font-size: 18px;
  margin: 0 2px;
  color: #7d2ae8;
}

.card-content .button{
  width: 100%;
  display: flex;
  justify-content: space-around;
  margin-top: 20px;
}

.card-content .button button{
  background: #7d2ae8;
  outline: none;
  border: none;
  color: #fff;
  padding: 8px 22px;
  border-radius: 20px;
  font-size: 14px;
  transition: all 0.3s ease;
  cursor: pointer;
}

.button button:hover{
  background: #6616d0;
}

.swiper-pagination{
  position: absolute;
}

.swiper-pagination-bullet{
  height: 7px;
  width: 26px;
  border-radius: 25px;
  background: #7d2ae8;
}

.swiper-button-next, .swiper-button-prev{
  opacity: 0.7;
  color: #7d2ae8;
  transition: all 0.3s ease;
}
.swiper-button-next:hover, .swiper-button-prev:hover{
  opacity: 1;
  color: #7d2ae8;
}


</style>
