let menuel = document.querySelector(".toggle");
let links = document.querySelector(".link");
let theheader = document.querySelector(".scroll"); // Fixed spelling
let element = document.querySelector(".logo h4");
let alllinks = document.querySelectorAll(".link a");
let nums = document.querySelectorAll(".number");
let section = document.querySelector(".box").offsetTop;
let imgel = document.querySelector(".parent");
let logo = document.querySelector(".image-logo");
let btn_one = document.querySelector(".one");
let btn_two = document.querySelector(".two");
let section_one = document.querySelector(".end");
let section_two = document.querySelector(".end_two");
let spanel = document.querySelector(".up");

menuel.onclick = function() {
    links.classList.toggle("active");
    if (links.classList.contains("active")) {
        menuel.classList.remove("fa-bars");
        menuel.classList.add("fa-x");
    } else {
        menuel.classList.add("fa-bars");
        menuel.classList.remove("fa-x");
    }
    if (window.scrollY >= 200) {
        menuel.classList.add("active");
    } else {
        menuel.classList.remove("active");
    }
};

window.onscroll = function() {
    if (window.scrollY >= 200) {
        theheader.classList.add("active");
        element.classList.add("active");
        menuel.classList.add("active");
        alllinks.forEach(link => link.classList.add("active"));
    } else {
        theheader.classList.remove("active");
        element.classList.remove("active");
        menuel.classList.remove("active");
        menuel.classList.remove("active");

        alllinks.forEach(link => link.classList.remove("active"));
    }
    nums.forEach((ele) => {
        let goal = parseInt(ele.dataset.goal);
        if (window.scrollY + window.innerHeight >= section && goal >= parseInt(ele.textContent)) {
            update(ele, goal);
        }

    })
    if (window.scrollY >= 500) {
        spanel.classList.add("active")
    } else {;
        spanel.classList.remove("active")

    }

};

function update(el, goal) {
    let curent = parseInt(el.textContent);
    let increament = Math.ceil(goal / 100);
    let timer = setInterval(() => {
        curent += increament;
        el.textContent = curent;
        if (curent >= goal) {
            el.textContent = goal
            clearInterval(timer)
        }

    })
}

function phone(ele) {
    imgel.src = ele
}
btn_two.onclick = function() {
    section_two.classList.add("active");
    section_one.classList.add("active");

}
btn_one.onclick = function() {
    section_two.classList.remove("active");
    section_one.classList.remove("active");

}
spanel.onclick = function() {
    window.scrollTo({
        top: 0,
        behavior: "smooth",
    });
}
document.addEventListener("DOMContentLoaded", function() {

    let allbox = document.querySelectorAll(".boxx");
    let section_last = document.querySelector(".contentt");
    let left = document.querySelector(".leftt");
    let right = document.querySelector(".rightt");
    let index = 1;
    let time;

    right.onclick = function() {
        index++;
        clearInterval(time);
        change();
    }

    left.onclick = function() {
        index--;
        clearInterval(time);
        change();
    }

    function change() {
        if (index > allbox.length) {
            index = 1;
        } else if (index < 1) {
            index = allbox.length;
        }
        section_last.style.transform = `translateX(-${(index - 1) * 100}%)`;
        // time = setInterval(() => {
        //     index++;
        //     change();
        // }, 3000);
    };
});