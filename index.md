<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Longni John Tao & Co.</title>
    <!-- <link href="https://www.littlesnippets.net/css/codepen-result.css" rel="stylesheet"> -->
    <link href="https://fonts.googleapis.com/css?family=Montserrat:400,500&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <link href="https://fonts.googleapis.com/css?family=Lato:300,400&display=swap" rel="stylesheet">
    <!-- AOS css -->
    <link rel="stylesheet" href="https://unpkg.com/aos@next/dist/aos.css" />
    <link rel="stylesheet" href="css/style.css">
    <!-- salJS script -->
    <link rel="stylesheet" href="./node_modules/sal.js/dist/sal.css">
    <script
        src="https://code.jquery.com/jquery-3.4.1.slim.min.js"
        integrity="sha256-pasqAKBDmFT4eHoN2ndd6lN370kFiGUFyTiUHWhU7k8="
        crossorigin="anonymous">
    </script>
    <!-- smooth scroll js-->
    <script src="https://cdn.jsdelivr.net/gh/cferdinandi/smooth-scroll@15.0.0/dist/smooth-scroll.polyfills.min.js"></script>
<style>
/*services detailed*/
.full-menu, .full-menu2, .full-menu3, .full-menu4, .full-menu5, .full-menu6{
    font-family: 'Montserrat', sans-serif;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 20;
    height: 80%;
    text-align: justify;
    margin-bottom: 200px;
    padding: 50px 80px 150px;
    overflow-x: hidden;
    overflow-y: scroll;
    background-size: cover;
    opacity: 0;
    visibility: hidden;   
    transition: opacity 0.3s 0s, visibility 0s 0.3s;
    color: whitesmoke;
}
.full-menu6,.full-menu2{
    overflow:hidden;
    width: 90%;
}
.full-menu .modal-close, .full-menu2 .modal-close, .full-menu3 .modal-close, .full-menu4 .modal-close, .full-menu5 .modal-close, .full-menu6 .modal-close {
    /* 'X' icon */
    position: absolute;
    z-index: 30;
    top: 0;
    right: 0;
    padding: 50px 80px 50px;
    height: 50px;
    width: 50px;
    border-radius: 50%;
    background:rgba(0, 0, 0, 0.3) url(cd-icon-close.svg)no-repeat center center;
    overflow: hidden;
    text-indent: 100%;
    white-space: nowrap;
    visibility: hidden;
    opacity: 0;     
    transform: scale(0);
    visibility: 0s 0.3s, opacity 0.3s 0s;
    transition: transform 0.3s 0s, visibility 0s 0.3s, opacity 0.3s 0s;
}
.full-menu.visible, .full-menu2.visible, .full-menu3.visible, .full-menu4.visible, .full-menu5.visible, .full-menu6.visible {
    background-size: 100%;
    opacity: 1;
    visibility: visible;   
    transition: opacity 0.7s, visibility 0s;
}
/*uncomment if scroll required within the service description*/
.full-menu.visible .fullmenu-content, .full-menu2.visible .fullmenu2-content, .full-menu3.visible .fullmenu3-content, .full-menu4.visible .fullmenu4-content, .full-menu5.visible .fullmenu5-content, .full-menu6.visible .fullmenu6-content {
    -webkit-overflow-scrolling: touch;
}
.full-menu.visible .modal-close, .full-menu2.visible .modal-close, .full-menu3.visible .modal-close, .full-menu4.visible .modal-close, .full-menu5.visible .modal-close, .full-menu6.visible .modal-close {
    visibility: visible;
    opacity: 1;    
    transition: transform 0.3s 0s, visibility 0s 0s, opacity 0.3s 0s;     
    transform: scale(1);
}
.full-menu.visible .fullmenu-content {
    -webkit-overflow-scrolling: touch;
}

@media only screen and (min-width: 1100px) {
    .full-menu .fullmenu-content {
        padding: 6em 5%;
    }
    .full-menu .fullmenu-content, .full-menu2 .fullmenu2-content, .full-menu2 .fullmenu2-content, .full-menu3 .fullmenu3-content, .full-menu4 .fullmenu4-content, .full-menu5 .fullmenu5-content, .full-menu6 .fullmenu6-content {
        padding: 6em 5%;
    }
    .full-menu .modal-close, .full-menu2 .modal-close, .full-menu3 .modal-close, .full-menu4 .modal-close, .full-menu5 .modal-close, .full-menu6 .modal-close {
        height: 60px;
        width: 60px;
    }
    .full-menu p, .full-menu2 p, .full-menu3 p, .full-menu4 p, .full-menu5 p, .full-menu6 p{
        font-size: 25px;
    }
}
/*smokey effect layer*/
.cd-transition-layer {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 2;
    height: 100%;
    width: 100%;
    opacity: 0;
    visibility: hidden;
    overflow: hidden;
}
.cd-transition-layer .bg-layer {
    position: absolute;
    left: 50%;
    top: 50%;
    -webkit-transform: translateY(-50%) translateX(-2%);   
    transform: translateY(-50%) translateX(-2%);     
    height: 100%;
    /* our sprite is composed of 25 frames */
    width: 2500%;
    background: url(ink.png) no-repeat 0 0;
    background-size: 100% 100%;
}
.cd-transition-layer.visible {
    opacity: 1;
    visibility: visible;
}
.cd-transition-layer.opening .bg-layer {     
    animation: cd-sequence 1.0s steps(24);     
    animation-fill-mode: forwards;
}

.cd-transition-layer.closing .bg-layer {     
    animation: cd-sequence-reverse 1.0s steps(24);    
    animation-fill-mode: forwards;
}
.no-cssanimations .cd-transition-layer {
    display: none;
}
@keyframes cd-sequence {
    0% {
        transform: translateY(-50%) translateX(-2%);
    }
    100% {        
        transform: translateY(-50%) translateX(-98%);
    }
}
@keyframes cd-sequence-reverse {
    0% {
         
        transform: translateY(-50%) translateX(-98%);
    }
    100% {
         
        transform: translateY(-50%) translateX(-2%);
    }
}

    </style>
</head>


<body oncontextmenu="return false">  
    <!--######### Nav bar ############-->
    <div class="wrapper">
        <header>
            <nav>
                <div class="menu-icon">
                    <i class="fa fa-bars fa-2x"></i>
                </div>
                <div class="logo">
                    L J T
                </div>
                <div class="menu"></div>
                    <ul>
                        <li><a href="http://longnitao.com/">Home</a></li>
                        <li><a href="#jump2service">Services</a></li>
                        <li><a href="#jump2about">About</a></li>
                        <li><a href="#jump2contact">Contact</a></li>
                    </ul>
                </div>
            </nav>
        </header>
    </div>

    <!-- main page starts here-->
    <div class="pimg1">
        <div data-sal-duration="1200"
        data-sal="zoom-out"
        data-sal-delay="300"
        data-sal-easing="ease-out-bounce"
        class="ptext">
            <span class="border">
                longni john tao & co.
            </span>
        </div>
        <div data-sal-duration="1200"
        data-sal="zoom-out"
        data-sal-delay="300"
        data-sal-easing="ease-out-bounce"
        class="ptext2">
            <span class="border2">
            <br>
            <br>
                chartered accountants
            </span>
        </div>
    </div>
    <section class="section section-light">
    </section>

    <!-- smoke animation starts here-->
    <div class="cd-transition-layer visible opening"> 
        <div class="bg-layer"></div>
    </div>

    <div class="full-menu" >
            <h3 style="text-align: center; font-size: larger; text-transform: uppercase;">Start-up services</h3>
            <br>
                Our services to “start-up” units in North Eastern States of India combine the in-depth knowledge of various sections of the industry in combination of advice on company law matters, such as which type of business association is most appropriate, tax holidays and exemptions available, how to set up a company, how the company is to be managed, employment law matters and duties of directors, and documents needed to run the company, such as minutes of meetings, constitutional documents, shareholders agreement, and contracts with suppliers and customers.
            <ul>
                <li>Incorporation of Companies and Limited Liability Partnership (LLP)</li>
                <li>Formation and registration of Society, Trust, Partnership, Clubs etc</li>
                <li>FCRA registrations, compliance and filing of periodical returns.</li>
                <li>Drafting of agreements – Rent agreement, Sales Deed, Partnership Deed, AOA, MOA, Trust</li>
                <li>Deed, LLP Deed etc.</li>
                <li>Digital signature certificates (DSC) and DIN.</li>
                <li>egistration under Shops and Establishment Act 1972,</li>
                <li>Obtaining license – Food, Trade, IEC, Trademark etc.</li>
                <li>FSSAI certificate</li>
                <li>Organic certified</li>
                <li>MSME registration</li>
                <li>2AA, 80G registration</li>
                <li>NITI AAYOG registration</li>
            </ul>
        <a href="#0" class="modal-close"></a>
    </div>
    <div class="full-menu2">
        <h3 style="text-align: center; font-size: larger; text-transform: uppercase;">Accounting and business process outsourcing</h3>
        <br>
            We endeavor and focus to increase the profitability and efficiency of our clients in providing the following services.
        <ul>
            <li>Complete End to end accounting – Tally software, Quickbooks & Bookkeeper</li>
            <li>Book-keeping.</li>
            <li>Year-end financial reporting.</li>
            <li>Consolidation and management accounting</li>
            <li>Administration of Fixed Assets Register, Payroll and Bank Reconciliatio</li>
            <li>Invoicing of sales and accounts receivable</li>
            <li>Staffing solutions</li>
            <li>Budgeting and management reporting</li>
            <li>Company secretarial services</li>
            <li>Improved internal control</li>
            <li>Part time CFO services:
                <ul>
                    <li>Preparation and explanations of management accounts.</li>
                    <li>Cash flow projections.</li>
                    <li>Budgeting – interim and annual.</li>
                    <li>verview of bookkeeping and month end closes.</li>
                    <li>Debtor and creditor management.</li>
                    <li>Project management of the financial component of new ventures.</li>
                    <li>Compliance management – corporate, taxation and other laws.</li>
                    <li>Review and assessment of internal controls</li>
                    <li>Revenue management, working capital management, MIS and Analytics</li>
                </ul>
            </li>
        </ul>
        <a href="#0" class="modal-close"></a>
    </div>
    <div class="full-menu3">
        <h3 style="text-align: center; font-size: larger;text-transform: uppercase;">Audit and assurance</h3>
        <br>
        The proprietor has vast and varied experience in conducting all types of Audits for large & medium sized business entities under IGAAP, IND AS and IFRS. We provide the following audit and assurance services:
        <ul>
            <li>Statutory Audit under Companies Act</li>
            <li>Audit of Partnership, Schools, Trust, Societies etc</li>
            <li>Tax Audit under Income Tax Act</li>
            <li>Internal Audit and Management audit</li>
            <li>Bank Auditing</li>
            <li>Proprietary Audit</li>
            <li>Individuals and contractors audit</li>
            <li>Stock Audit</li>
            <li>GST Audit</li>
            <li>Certifications and due diligence.</li>
        </ul>
        <a href="#0" class="modal-close"></a>
    </div>
    <div class="full-menu4">
        <h3 style="text-align: center;font-size: larger;text-transform: uppercase;">Taxation</h3>
        <br>
            Today, from individuals to firms or to corporate, all require to comply with numerous direct tax and indirect laws which are complicated and need to be completed in a time bound and efficient manner. We provide the following types of services in Direct and Indirect taxation.
        <ul>
            <li>Indirect taxation:
                <ol>
                    <li>Tax planning and management</li>
                    <li>Filing of return of income, tax deducted at source etc.</li>
                    <li>Compliances of advance tax/TDS rules and regulations</li>
                    <li>Obtaining TDS exemption certificates.</li>
                    <li>Professional tax</li>
                    <li>Representing client before various tax authorities for assessments, appeals, and search & seizure cases.</li>
                    <li>Personal taxation – tax returns, tax assessment, wealth management and VISA procedure.</li>
                </ul>
            </li>
            <li>Indirect taxation:
                <ol>
                    <li>Registration of GST</li>
                    <li>Ascertainment of tax liability</li>
                    <li>Filing of returns,</li>
                    <li>Representing client before various tax authorities for assessments, appeals and search & seizure cases.</li>
                </ol>
            </li>
        </ul>
        <a href="#0" class="modal-close"></a>
    </div>
    <div class="full-menu5">
        <h3 style="text-align: center; font-size: larger;text-transform: uppercase;">Project consulting</h3>
        <br>
            Finance is the bloodline for any business and we carefully analyse the current needs and situation and accordingly help prepare project reports to arrange finance in the form of working capital, cash credit, project loans and term loans from Banks and financial institutions. We also offer due diligence for finance.
            <br>
            We prepare claim for various subsidies available from the Central as well as State Governments and render certification services:
        <ul>
            <li>Preparation of project reports.</li>
            <li>Loan arrangement/ Loan syndication – working capital, cash credit limit, term loan & project loan.</li>
            <li>Certifications requirement.</li>
            <li>Due diligence for finance.</li>
            <li>Consultancy for subsidy, concession loan and grant in aid available.</li>
            <li>Preparation of all documents for filling of subsidy claim.</li>
            <li>Certification of certificates to be filed along with subsidy claims.</li>
            <li>Representing the client for clarification to the Government Authorities.</li>
        </ul>
        <a href="#0" class="modal-close"></a>
    </div>
    <div class="full-menu6">
        <h3 style="text-align: center; font-size: larger;text-transform: uppercase;">Secretarial compliances</h3>
        <br>
        <ul>
            <li>Compliance and assisting in maintaining statutory registers and records.</li>
            <li>Filing of required documents with the ROC etc.</li>   
            <li>Filing of annual return & annual accounts.</li>
        </ul>
        <a href="#0" class="modal-close"></a>
    </div>


    <div class="pimg2" id="jump2service">
        <div class="ptext" data-aos="fade-down" data-aos-offset="100">
            <span class="border">
                Services
            </span>
        </div>
    </div>
<section class="services-sect">
      
    <div class="container">
        <section class="card1" data-aos="fade-right">
          <img src="./images/startup.jpg">
          <div class="caption">Click to learn about this service in detail</div>
            <h3>STARTUP SERVICES</h3>
            <a href="#"></a>
        </section>

        <section class="card2" data-aos="fade-left" >
          <img src="./images/accounting.jpg">
          <div class="caption">Click to learn about this service in detail</div>
              <h3>ACCOUNTING & BUSINESS PROCESS OUTSOURCING</h3>
            <a href="#"></a>
        </section>

        <section class="card3" data-aos="fade-right">
          <img src="./images/audit.jpg">
          <div class="caption">Click to learn about this service in detail</div>
            <h3>AUDIT AND ASSURANCE</h3>
          <a href="#"></a>
        </section>

        <section class="card4" data-aos="fade-left">
          <img src="./images/taxation.jpg">
          <div class="caption">Click to learn about this service in detail</div>
            <h3>TAXATION</h3>
            <a href="#"></a>
        </section>

        <section class="card5" data-aos="fade-right">
          <img src="./images/consultancy.jpg">
          <div class="caption">Click to learn about this service in detail</div>
            <h3>PROJECT CONSULTANCY</h3>
          <a href="#"></a>
        </section>

        <section class="card6" data-aos="fade-left">
          <img src="./images/complaince.jpg">
          <<div class="caption">Click to learn about this service in detail</div>
            <h3>SECRETARIAL COMPLAINCE</h3>
            <a href="#"></a>
        </section>   
    </div>
        
</section>

    <div class="pimg3" id="jump2about">
        <div class="ptext">
            <span class="border" data-aos="fade-down" data-aos-offset="100">
                About Us
            </span>
        </div>
    </div>
    <section class="section section-dark">
        <h2>Founder & Proprietor</h2>
        <p data-sal-duration="1200"
        data-sal="zoom-out"
        data-sal-delay="300"
        data-sal-easing="ease-out-bounce" style="text-align: center;">
        CA Longni John Tao, B. Com (H), FCA is a fellow member of the Institute of Chartered Accountants of India (ICAI). He acquired his member in 2013 and have worked in a leading audit and tax consulting firm viz. Deloitte for more than 5 years in Bangalore. He is extensively involved in audits under IGAAP, IFRS and Tax audit under Income Tax Act 1961 both for listed and unlisted Companies. He has also knowledge in statutory audit of bank branches, risk based internal control audit and GST audit. Further he has also large knowledge in certifications both statutory and specific, end-to-end accounting and statutory compliances and project reviews. He is the first Chartered Accountant from Senapati District Manipur.
        </p>
    </section>

    <div class="pimg4"></div>

    <section class="section section-dark">
        <h2>Our Vision</h2>
        <p data-sal-duration="1200"
        data-sal="zoom-out"
        data-sal-delay="300"
        data-sal-easing="ease-out-bounce" style="text-align: center;">
        We value an act with high standards of HONESTY and INTEGRITY for success in all the areas of life including profession and the firm.
        <br>
        <br>
        We strive to continuously improve our QUALITY of service.
        <br>
        <br>
        We are committed to create an IMPACT that matters to one another and for the society as a whole.
        </p>
    </section>
    
    <div class="pimg5"></div>

    <section class="section section-dark" >
        <h2>Our mission</h2>
        <p data-sal-duration="1200"
        data-sal="zoom-out"
        data-sal-delay="300"
        data-sal-easing="ease-out-bounce" style="text-align: center;">
        We will predominantly work with organization in the North East India region as partners to help them achieve their desired outcomes from the growing market. We will build trust and provide our customer with guidance to the solution we believe is the best-in-practice.
        <br><br>
        Our focus is help start-ups and other small & medium sized business owners in starting, managing andgrowing their business with compliance and profitability.
        </p>
    </section>

<div class="form-box">   
    <h2 style="text-align: center; font-family: 'Montserrat', sans-serif; color: black;">Mail us your concerns</h2>
    <div class="wpcf7" id="wpcf7-f156-p143-o1 formwrap" 
    data-sal-duration="1200"
    data-sal="slide-left"
    data-sal-delay="300"
    data-sal-easing="ease-out-bounce">
        <form action="/?page_id=143#wpcf7-f156-p143-o1" method="post" class="wpcf7-form" novalidate="novalidate">
            <div style="display: none;">
                <input type="hidden" name="_wpcf7" value="156">
                <input type="hidden" name="_wpcf7_version" value="3.7.2">
                <input type="hidden" name="_wpcf7_locale" value="en_US">
                <input type="hidden" name="_wpcf7_unit_tag" value="wpcf7-f156-p143-o1">
                <input type="hidden" name="_wpnonce" value="d1da331d93">
            </div>
            <p>
               <span class="wpcf7-form-control-wrap Name">
                 <input type="text" name="Name" value="" size="40" class="nameinput wpcf7-form-control wpcf7-text wpcf7-validates-as-required" aria-required="true" aria-invalid="false" placeholder="Name">
              </span>
              <span class="wpcf7-form-control-wrap Email">
                <input type="email" name="Email"  size="40" class="emailinput wpcf7-form-control wpcf7-text wpcf7-email wpcf7-validates-as-required wpcf7-validates-as-email" aria-required="true" aria-invalid="false" placeholder="Email">
              </span>
              <span class="wpcf7-form-control-wrap Subject">
                <input type="text" name="Subject"  value="" size="40" class="subjectinput wpcf7-form-control wpcf7-text wpcf7-validates-as-required" aria-required="true" aria-invalid="false" placeholder="Subject">
              </span>
              <!-- <span class="wpcf7-form-control-wrap Subject flat">
                <select name="Subject" class="indent wpcf7-form-control wpcf7-select wpcf7-validates-as-required" aria-required="true" aria-invalid="false">
                  <option value="General">General</option>
                  <option value="Booking">Booking</option>
                </select>
              </span> -->
              <span class="wpcf7-form-control-wrap Message">
                <textarea name="Message" cols="40" rows="10" class="wpcf7-form-control wpcf7-textarea" aria-invalid="false" placeholder="Message"></textarea>
              </span>
              <input type="submit" value="Send" class="wpcf7-form-control wpcf7-submit btn">
              <img class="ajax-loader" src="http://www.jordancundiff.com/wp-content/plugins/contact-form-7/images/ajax-loader.gif" alt="Sending ..." style="visibility: hidden;">
          </p>
          <div class="wpcf7-response-output wpcf7-display-none">
          </div>
      </form>
    </div>
</div>

    <div class="pimglast" id="jump2contact">
        <div class="last-container">
            <section class="contact" data-aos="fade-left">
                <h2>Contact Us</h2>
		<h3>Email: ljt@longnitao.com<h3>
                <section class="address" data-aos="fade-left">
                    <h3>Address</h3>
                        1st Floor, Next to St. Anthony's Jr. Block Building,<br>
                        near Broadway Complex, NH-2<br>
                        Senapati District HQ<br>
                        Pin-Code: 795 106<br>
                        City- Imphal, Manipur, India.<br>
                        Tel: 03871 222566
                </section>
                <section class="hours" data-aos="fade-left">
                    <h3>Working Hours</h3>
                        Monday - Saturday: 10:00AM - 05:00PM
                </section>
            </section>

            <section class="links" >
                <h2 style="text-align: center;" data-aos="fade-right">Related Links</h2>
                <section class="col1">
                    <ul>
                        <li data-aos="fade-right"><a href="http://www.incometaxindia.giv.in/">Income Tax of India</a></li>
                        <li data-aos="fade-right"><a href="http://www.mca.gov.in/">Companies Act of India</a></li>
                        <li data-aos="fade-right"><a href="http://www.dipp.nic.in/">Ministry of Udyog</a></li>
                        <li data-aos="fade-right"><a href="http://www.rbi.org.in/">Reserve Bank of India</a></li>
                        <li data-aos="fade-right"><a href="http://www.gst.gov.in/">Goods and Service Tax</a></li>
                        <li data-aos="fade-right"><a href="http://www.dgft.delhi.nic.in/">Directorate General of Foreign Trade</a></li>
                    </ul>  
                </section>
                <section class="col2">
                    <ul>
                        <li data-aos="fade-right"><a href="http://www.finmin.nic.in/">Ministry of Finance</a></li>
                        <li data-aos="fade-right"><a href="https://msme.gov.in/">MSME</a></li>
                        <li data-aos="fade-right"><a href="http://www.kvic.org.in/">Khadi and Village Industries Commission</a></li>
                        <li data-aos="fade-right"><a href="http://www.necouncil.gov.in/">North Eastern Council</a></li>
                        <li data-aos="fade-right"><a href="https://mdoner.gov.in/">DONER</a></li>
                    </ul>
                </section>
            </section>
        </div>
        <hr>
        <section class="cpy" data-sal-duration="1200"
        data-sal="fade-down"
        data-sal-delay="300"
        data-sal-easing="ease-out-bounce">
            <p style="text-align: center; color: black;"><strong>© 2020 Longni John Tao & Co. | All Rights Reserved</strong></p>
            <section class="giticon">
            <a href="https://github.com/S-T-R-i-F-E"><i class="fa fa-github" style="font-size:36px"></i></a>
            </section>
            <section class="gitname">
                webpage created by: S-T-R-i-F-E(Benson Kho)
            </section>
        </section>
    </div>

    <script src="./node_modules/sal.js/dist/sal.js"></script>
    <script>
        sal();
    </script>

    <script src="https://cdn.jsdelivr.net/npm/lax.js" ></script>
    <script>window.onload = function() {
        lax.setup() // init
    
        const updateLax = () => {
            lax.update(window.scrollY)
            window.requestAnimationFrame(updateLax)
        }
    
        window.requestAnimationFrame(updateLax)
    }
    </script>  

    <!-- ###### AOS script ##########-->
    <script src="https://unpkg.com/aos@next/dist/aos.js"></script>
    <script>
      AOS.init({
          offset:180,
          easing:'ease-in-out',
          duration:500,
      });
    </script> 

<script type="text/javascript">
   // Menu-toggle button
   $(document).ready(function() {
          $(".menu-icon").on("click", function() {
                $("nav ul").toggleClass("showing");
          });
    });

    // Scrolling Effect
    $(window).on("scroll", function() {
          if($(window).scrollTop()) {
                $('nav').addClass('black');
                $('nav ul li a').addClass('black');
                $('.logo').addClass('black');
          }

          else {
                $('nav').removeClass('black');
                $('nav ul li a').removeClass('black');
                $('.logo').removeClass('black');
          }
    });
</script>

<script src="jquery-2.1.4.min.js"></script> 
<script type="text/javascript">
    'use strict'; 
   //hover effect
    $(".hover").mouseleave(
  function () {
    $(this).removeClass("hover");
  }
);


   $(document).ready( function() {
    
       var width = 100,
           perfData = window.performance.timing, 
           EstimatedTime = -(perfData.loadEventEnd - perfData.navigationStart),
           time = ((EstimatedTime/1000)%50) * 100
   
   
       // Percentage Increment Animation
       var PercentageID = $(".percentage"),
               start = 0,
               end = 100,
               durataion = time;
               animateValue(PercentageID, start, end, durataion);
   
       function animateValue(id, start, end, duration) {
   
           var range = end - start,
             current = start,
             increment = end > start? 1 : -1,
             stepTime = Math.abs(Math.floor(duration / range)),
             obj = $(id);
   
   
           var timer = setInterval(function() {
               current += increment;
               $(obj).text(current);
             //obj.innerHTML = current;
               if (current == end) {
                   clearInterval(timer);
               }
           }, stepTime);
       }
       
   
       
       setTimeout(function(){
           $('.preloader').fadeOut();
           
           $('.cd-transition-layer').addClass('closing').delay(1000).queue(function(){
               $(this).removeClass("visible closing opening").dequeue();
           });
           
       }, time);
   });  
   
   
   $(window).load( function() {
   
   function smokeeffect () { 
    var modalTrigger = $('.card1'),
           transitionLayer = $('.cd-transition-layer'),
           transitionBackground = transitionLayer.children(),
           modalWindow = $('.full-menu');
       
    var modalTrigger2 = $('.card2'),
        modalWindow2 =$('.full-menu2'),
        modalTrigger3 = $('.card3'),
        modalWindow3=$('.full-menu3'),
        modalTrigger4 = $('.card4'),
        modalWindow4 =$('.full-menu4'),
        modalTrigger5 = $('.card5'),
        modalWindow5 =$('.full-menu5'),
        modalTrigger6 = $('.card6'),
        modalWindow6 =$('.full-menu6');
   
       var frameProportion = 1.78, //png frame aspect ratio
           frames = 25, //number of png frames
           resize = false;
   
       //set transitionBackground dimentions
       setLayerDimensions();
       $(window).on('resize', function(){
           if( !resize ) {
               resize = true;
               (!window.requestAnimationFrame) ? setTimeout(setLayerDimensions, 300) : window.requestAnimationFrame(setLayerDimensions);
           }
       });
   
       //open modal window
       modalTrigger.on('click', function(event){   
           event.preventDefault();
           transitionLayer.addClass('visible opening');
           var delay = ( $('.no-cssanimations').length > 0 ) ? 0 : 600;
           setTimeout(function(){
               modalWindow.addClass('visible');
           }, delay);
       });
       modalTrigger2.on('click', function(event){   
           event.preventDefault();
           transitionLayer.addClass('visible opening');
           var delay = ( $('.no-cssanimations').length > 0 ) ? 0 : 600;
           setTimeout(function(){
               modalWindow2.addClass('visible');
           }, delay);
       });
       modalTrigger3.on('click', function(event){   
            event.preventDefault();
            transitionLayer.addClass('visible opening');
            var delay = ( $('.no-cssanimations').length > 0 ) ? 0 : 600;
            setTimeout(function(){
                modalWindow3.addClass('visible');
            }, delay);
        });
        modalTrigger4.on('click', function(event){   
            event.preventDefault();
            transitionLayer.addClass('visible opening');
            var delay = ( $('.no-cssanimations').length > 0 ) ? 0 : 600;
            setTimeout(function(){
                modalWindow4.addClass('visible');
            }, delay);
        });
        modalTrigger5.on('click', function(event){   
            event.preventDefault();
            transitionLayer.addClass('visible opening');
            var delay = ( $('.no-cssanimations').length > 0 ) ? 0 : 600;
            setTimeout(function(){
                modalWindow5.addClass('visible');
            }, delay);
        });
        modalTrigger6.on('click', function(event){   
            event.preventDefault();
            transitionLayer.addClass('visible opening');
            var delay = ( $('.no-cssanimations').length > 0 ) ? 0 : 600;
            setTimeout(function(){
                modalWindow6.addClass('visible');
            }, delay);
        });
   
       //close modal window
       modalWindow.on('click', '.modal-close', function(event){
           event.preventDefault();
           transitionLayer.addClass('closing');
           modalWindow.removeClass('visible');
           transitionBackground.one('webkitAnimationEnd oanimationend msAnimationEnd animationend', function(){
               transitionLayer.removeClass('closing opening visible');
               transitionBackground.off('webkitAnimationEnd oanimationend msAnimationEnd animationend');
           });
       });
       modalWindow2.on('click', '.modal-close', function(event){
           event.preventDefault();
           transitionLayer.addClass('closing');
           modalWindow2.removeClass('visible');
           transitionBackground.one('webkitAnimationEnd oanimationend msAnimationEnd animationend', function(){
               transitionLayer.removeClass('closing opening visible');
               transitionBackground.off('webkitAnimationEnd oanimationend msAnimationEnd animationend');
           });
       });
       modalWindow3.on('click', '.modal-close', function(event){
            event.preventDefault();
            transitionLayer.addClass('closing');
            modalWindow3.removeClass('visible');
            transitionBackground.one('webkitAnimationEnd oanimationend msAnimationEnd animationend', function(){
                transitionLayer.removeClass('closing opening visible');
                transitionBackground.off('webkitAnimationEnd oanimationend msAnimationEnd animationend');
            });
        });
        modalWindow4.on('click', '.modal-close', function(event){
            event.preventDefault();
            transitionLayer.addClass('closing');
            modalWindow4.removeClass('visible');
            transitionBackground.one('webkitAnimationEnd oanimationend msAnimationEnd animationend', function(){
                transitionLayer.removeClass('closing opening visible');
                transitionBackground.off('webkitAnimationEnd oanimationend msAnimationEnd animationend');
            });
        });
        modalWindow5.on('click', '.modal-close', function(event){
            event.preventDefault();
            transitionLayer.addClass('closing');
            modalWindow5.removeClass('visible');
            transitionBackground.one('webkitAnimationEnd oanimationend msAnimationEnd animationend', function(){
                transitionLayer.removeClass('closing opening visible');
                transitionBackground.off('webkitAnimationEnd oanimationend msAnimationEnd animationend');
            });
        });
        modalWindow6.on('click', '.modal-close', function(event){
            event.preventDefault();
            transitionLayer.addClass('closing');
            modalWindow6.removeClass('visible');
            transitionBackground.one('webkitAnimationEnd oanimationend msAnimationEnd animationend', function(){
                transitionLayer.removeClass('closing opening visible');
                transitionBackground.off('webkitAnimationEnd oanimationend msAnimationEnd animationend');
            });
        });

   
       function setLayerDimensions() {
           var windowWidth = $(window).width(),
               windowHeight = $(window).height(),
               layerHeight, layerWidth;
   
           if( windowWidth/windowHeight > frameProportion ) {
               layerWidth = windowWidth;
               layerHeight = layerWidth/frameProportion;
           } else {
               layerHeight = windowHeight*1.2;
               layerWidth = layerHeight*frameProportion;
           }
   
           transitionBackground.css({
               'width': layerWidth*frames+'px',
               'height': layerHeight+'px',
           });
   
           resize = false;
       }
   
   }
   smokeeffect()
   }); // document load end 
</script>

<script>
    //smoothscroll
	var scroll = new SmoothScroll('a[href*="#"]');
</script>

<script type="text/javascript">
//disble keyboard shortcuts
    var isNS = (navigator.appName == "Netscape") ? 1 : 0;
    
    if(navigator.appName == "Netscape") document.captureEvents(Event.MOUSEDOWN||Event.MOUSEUP);
    
    function mischandler(){
    return false;
    }
    
    function mousehandler(e){
    var myevent = (isNS) ? e : event;
    var eventbutton = (isNS) ? myevent.which : myevent.button;
    if((eventbutton==2)||(eventbutton==3)) return false;
    }
    document.oncontextmenu = mischandler;
    document.onmousedown = mousehandler;
    document.onmouseup = mousehandler;
    var isCtrl = false;
    document.onkeyup=function(e)
    {
    if(e.which == 17)
    isCtrl=false;
    }
    
    document.onkeydown=function(e)
    {
    if(e.which == 17)
    isCtrl=true;
    if(((e.which == 85) || (e.which == 117) || (e.which == 65) || (e.which == 97) || (e.which == 67) || (e.which == 99)) && isCtrl == true)
    {
    // alert(‘Keyboard shortcuts are cool!’);
    return false;
    }
    if (event.keyCode == 123) { // Prevent F12
        return false;
    } else if (event.ctrlKey && event.shiftKey && event.keyCode == 73) { // Prevent Ctrl+Shift+I        
        return false;
    }
    }
    
</script>
</body>
</html>
