<script setup>
import { ref,computed  } from 'vue';


//variable drinking
const travelList=ref([
  {name: 'สุนทรารมณ์',  price:500, img:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHCBQUFBcUFBUYFxcZGhocGhkaGhkaHBwYHBkaISAaIxoaICwjGxwoIBcgJDUkKC0vMjIyGiI4PTgxPCwxMi8BCwsLDw4PHRERHDEoIygxMTEzMTExMTExMjE0MTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMf/AABEIAOAA4AMBIgACEQEDEQH/xAAcAAABBQEBAQAAAAAAAAAAAAAFAAIDBAYHAQj/xABIEAACAQIEAwUEBwQIBQMFAAABAhEAAwQSITEFQVEGEyJhcYGRobEHMkJSwdHwFCNT4RczYnKCk6PSFSSSsvFUouJDRGNzg//EABoBAAIDAQEAAAAAAAAAAAAAAAADAQIEBQb/xAAuEQACAgEEAQMEAQIHAAAAAAABAgARAwQSITFBE1FhBSIycRSBkRVCUsHh8PH/2gAMAwEAAhEDEQA/AOzUqVKiEVKlSohFSpUqITylTHcASTFUb3EOSj2n8qozqvcsFJ6hAsBVW7jkHOfT86F3bjN9Yk1HWZtT/pEaMPvL78RPJR7aqYvihQSzxOwEAn0qAXVJgMCegIrl3abjAu3yzNCglLY8gd/adZ9KUcjk9zfpNGuR/u4A7Jh7jPajEOXNq5lRSqgj62xkyfPpVC5xHELZS6uIvZi0GXJGxnQ6bigty5IAAgACfNgN6KYTDteC2yMiC27Lro1wDefU/Ol7mJ7nfOlw4kH2iv14hPhPbS4CFvksv310YeZA0b2R7a2X/GFVQ/fqFYSCWGo6ia5I1lhupHqDTKgZGHmUzfSMOVtyce87LhOPLc0t3LdyN4IJj/CaIWuKKfrKR6aiuTdj3ZcUuUFgVYNGwX7x9oFdDa6uYLmGYgkLIkgc46U1c7jzOFrNEuHJsHM0VnEK31WB+fuqaspexlpD47iIfN1B+Jq/guLBvqurjyYH4inrqAexMTaZgLEOUqgs4hW2OvTnU9aQQeRM5FT2lSpVMIqVKlRCKlSpUQipUqVEIqVKvKIRVSxWOVNBq3Tp61Wx3EN1Q+rfl+dDgKzZc23he41Md8mT3L7MZY0x3ABPICfdTSaH8Zvutsi2AWYgQenM1iYk8masePcwUS/h7udQ0RM/M1muL8Ydr4sW9ArKH+8x0MDkFA3JonwvGhbapcMEDU7g+4VhsZxT99edApzkgPqCF2010MR7qAROlpNMWyMK66k/HLXd4sF2YpoQVOy+Ubaj40JxlyyxxN421VUQJaBWQTu0Dk7ZhryAqN7hYyxmAB6AbDyFCFuG9dEE92pzAci6xr8R7BTsPJJ8TdrcYVETtjx/zDwUfs9ubbKwAUvyYxrvqdfdVjBXcqhLilrbZiIJlSBqRGux2qrevvcKg8gAB7N/U1NYxT2o8KGddRr676Gkk83N4xn0gvcsi4lwlGclUMqZ+so5Hz8/OhLHmBHlVnE45n3VB5gQffNMayMisDuSpHQ7j4VUm4zEuzuFeBcfGGUr3QaTJYNDHpy2HSmce4mL7peTMpVcsTDAgkyCOXi3oNFEMBpautAOgAnr+iKgtQiW0uJX9SuZQJkkkySZJ5k9Zr1HKtmUlW6gkH3jammkKJrKL1XE23ZbtM7utm7qx+pcG8jk0eQ399bzDcQjR9fP86xHYrhQRO/ceNpCTyTqPU/CK1FPR2XqeP8AqC4jmIQUP95okcESDIp1A8LiSh6jmP1zoxauhhIrbjyBxOW6FZLSpUqbKRUqVKiEVKlSohGmhXEMZPhQ6cz+AqbiOKyjKu53PQfnQpRWbPlr7RHY0vkzwLTqdFMY1imi41qzPaFyL9pWYi2YkeYbX8KOYS28u7tJc6L9lFGwHU8yep6AVj+Lcet3lZXRldGbuyNQRqNenIn0qDN2ixMcnAsef6wzibubObYVioaAuxIBIHmTWafAXbtsM6hCoJGkM3P6oAApYHjzIArICFEAroZHM9T515j+O3GEo2VShzrCkzrOpE7EbVHBM62PDlxHgD9zM8SckLbXe4YnovM1BeQnwW/CiQGbnJ39dDJqy310ciBlI15EwRPyqRLQUOCRlYkydN9xWlG2gV/0xebCcrlif/AJQXDtauJ4yyuYO419J/UUWZwNyJPU71TRwyi4+gQH/q2Jj2fGvExVq6wUiT9nMPkajIGfkjruozTOmAbQwG48An+8LpjUW06P4QSCGAEz0M8qHft6fVz6b+U+tS3cPnUqQY5xy6UPXhbK2jCDoZHI+XOlKFI5mrK2RG+xbBmn7N2rOIZrLsAWHgcHZhy9tQcUwdzDubLyADIjZhybzqpw5UtMpjQTJG50InWnYi6zHUsQJChiTlE7UMV21LY0yeruJ4I5Hz8SKr3COGviLgtpMbs33V5n16edUaL8G40bBKhZRiCw2aY3Dc/Q/ClrV8xmpOQYj6YszpNjDi3bVLa6KsKvoNBrWcv9rgCVFhsw0IZwCCN9AvlVLG9sQbRS0rhzpmaPCOZEEyag7J4m/cvJlZmAYm6ORUrAcnmdI6mAetaEK+eZ5V9DmCnI/H7mx4RjO/ti5kKGYKmdPQkCQevrROxcKGRtzFOIqKZ1GoqLo2Jh+DDVu4GEjan0Kwt7KfI7/nRQGtuN9wmd12mOpUqVNlZ5UGJvZVLe7zPKp6D469meBsvz5n8PfS8j7VuWVbMquxJJOpO9NWnMK9UVzibM1CeGo2qVqjqITll+5dsXHtq9xMjMNGYaA6GJgyINR4u0YW4Y/eax5/zPzot20wpXEF4IV1UzyzDQj3AUH4teV1RUkhFgjbNtoOlVN7gJ63C941yIOa5qVoqK46yJbUGYn2SR7ad3crlbXz2+W1NsWFQQo33PP2mrDaI9i7UABXzJNCOoNQ23t5sq5cw5ACff+VSldDG529etZ7DOto52kupIyajWPrFto12En05uw4vUU0eph1+t/jMgZRR7PxDygZnWJBhoPnoR/wC341X/AGK2ty2VWDJO52A6T1IoY3FLklhAmOUwBy19vvqJuIXCQ2bUSNhsY5eytK6XIOb8TmZfq2lYAbbIPBrofEJ3cXeV9bYyzA0OxMA5piaJxQW3xacouDQGSRziY09Y51cwWP7xiAhAHOdP5GkZcLhbqqm/Q67EzEDITZ4B7Eu4S9BDlQSDqrbacj8PfRXG461fMshtudMykFT/AHhAPtGtBluKWZQfEIkVKqSQBudPfWVjXidIIrgOTyOLE9YRUT3MpjLM7fltRPjR/eBYHhUUX4Ms2EKR3qOxB8z9knoyEDy0PKmYAHJuZddndMYKmiZQ4PZw905T3pu/cMLP93Lr7yK1Nrhy2bOYWgAzRkN15YnqFJXYHnyqLC4UYkC4g/epdVgx0YKMuZD5ZQyx1BrXYrCpcTI0wCCCDBBGxH651tVQPE81qc7twSTMtw4tcw9x3J/clhGa6ZgSNc4g6x8edV+ErcNy7bLsgUZhka6VBJ1ESRrqZIPOtRhsDbAa2F8CmMp1zMQCzt94+IAdIqSzhEtjLbUKCZO8k+ZJk1NCYoFvHErDLcFwoSwDI0nQgrK21kEfEDpRXA9pYCi5aIEaNbZbgj+6DnHpBqFFa94sxS0CcuQ5WeNMxfdV3gLqRrOtCbfDsFcutbU548a5bjGBoGQzIMN4p/teVQHUdQKkzdYTG27glHDRuBuPVTqPbVmsFhuHWw58BtuDlDAsI+6fCR4W5FSNdDNHcNj7lsw5NxRuDBcL99SAO8XyIzaHUmAXA2LEXDGMvZEJ57D1O1B1q3xW5LKvQSfU6D5GqDPEdOZ6dD6VjztbVH4xQuSEVG7hfrED1IHzpxvLIE79NfZpzqpxRQ9s76Qdj7eXSaRUZJkvK31SG9DNeis3aushlTBq9gOPW7mYEg5GysV1AboR+U1JSWWzJ+Pd33LG8uZBExuJMAiOckVy68ILBDOpgkcusV1PjNtbuFugGQbbEEdQJHxFcpDZhKka7HcTVW8Tv/RyCjCz+pC19h4Y8UgajSDOunoR61Ojz5Hp/wCaBYzE3laHgEbEAQwnfXT4UxOJ3AdSCOYIA+I9K1/xCygiog/WVxOytftyI+7xJ5cKYUnTyHl60OJ+Nb3sl9HV3FAXsQTZstqqgfvXB5idEXzMk9NjXVeDdm8JhRFiyin75GZz6u0t8a1hkxClHM83ny5MzW7WPE+fMPwTF3INvC33B5rauEe8LFS3+zuNQS+ExAHXubke8LpX0oaq8Qsl7ZC76ED0NLbVMASBFpiVmAJnzG6FTlYFT0IIPuNOtXmScrEToYrq/bLh3eIHKzkkNI1Cn8jXMcZgTbPlyP62NGHWLlFMKm9vpuXGoy4mv9diEMLcVwjlgGXQkQsz9mK2uK4QrWFxWHnQAsm5UjcjrBrnnCrU3AGX7JIkab7+Y0PtrWDFBbaIjMrjNJBjRj9Xz0rLqAqsR2J3fp5zZMIYcG6Pz+4NxmORD42JY69T6mifCOIi34tSjCYG/VSJ56x6Hyoe9tW3AMdQD86u8NxCW3DuneKNlmBPI7ax0pCsq1t7nRz4cjqwaiPAHc0/Z67dt4l2YA50kqojwiNurdCd/aa2WIuFrbG2fFllCOZ3A9CRB9TWT4TxS1cuE20Kl4zBtcrAEgBuakKxjSCPPQ/hLmVsvJiSPJ9z7CBPqD1rcrbhYnjsyMmQqwowhgb4YsRs4W4voVAI9mUf9VLir5LN1huLbkeoQ1Rwj92SP4Tn/KueL3Cf9KiHELee3cTqjr71I/GpioI4o0W7VoQFYQf7qqIX26ewUG4ZhP8AnLZQQFBZo5DKR8Sfn0rSrZS7bTMJBVWGpBBKjUEajflXq4a3bRhAVIJadZEakk6nSs28AbfMZt5uD+J4+2LmXMuYp1nxBjlGmxBk+0UZujxoeeYj2ZGJ+Kg+ysnhcEmde8TwM0pmk5Enwow2BbQSfvEbjU8LptEyC1tQVtnci6wGW2x+Ablng1qxcLUS/cbfa53t585iSVB2KLppO22/U85q3bysAwUtI5/z/CqXE/6vUSdIPnvp7qfbvi2FtkM7AbJEQfjWNjuNzQOBH27wcm2GBjzO3rG4PP0qRWJlTlJGh9Dz5xNRYWzb8QRGB5gxInyJpuFwItyTmJPPQfJiapJga2gFwK4kBoPviuX8TS7g8Tdtq7Aq8g66iJRiDuQG+JrqfFEi5InUA6zvtz15VT7T9mFxyLdQhLwUQ2uVh91huNSYYSR0pqn3jcT7TOe8X7Q37yIpZkQr4kRiFdpIJIG40+qZFUcHjHUBAAddPU1JxHDtbRbbjLctvcRh5htfZqCPKm8JtSxb7o+JqXAC8zp6IN6gCGrhr9l7xCtxPCT4TBG3MH1plvDotwLbsIzArkJEw06GNm9GkaVoMNdy4e3K5tWgHbVmM+lFeymDz4wFlEd2bgEAaHwjQetUQt0DxGa30xuZwL5/rU0HZZcWuHVbgHh+qXYliPOPxNFTfvrvbVh/ZP8AP8Kjx/HsPZkPcGYfZXU/DageA7fYe40EMonfKYA6netFECyJ5NzvclT/AG6mutPIBIInkdxQLtH2mt4VY+vcP1VHXqfIUdRwwDKQQRII2IPOuNdsMSWxd3Nshyj03+ZNIykigJ0tBp1yvTdCVcdxDHY24QHIB+yugg9Y5epoVisPctl0ZhcAJDD8if1pRrBdqbdqyF7tydRmUKo9fFJY+cUAxHESSXVSQTqWOsn8fOqqG9p2gUSwDUntcaX9nt2SgzWi+Vo1YMZyzy1OvsoYmNdSzaS281YwnCLt5iLdsxPMRAPWdB7aO3+zCqw7xxrAbJmcqYABMRAJ01GhYedaBjvkiZW1pxgKp69pQs4pGUEsJ0kba+lWLfiMLJj9fjvRzA8As2z/AFeo53HRfgD8xRdLSBSuayinTKDmBB308NKOnF9zYv1d9v4yDsvg2R2FxcrAZl2IbkzSDuoaI/tE+mntrmdQORBbyA116E7AedVeFWEAC3HLFRKNmgFG6ldcwiCCTyPOiyMgAVIjkFGnrppTgAoqcDPkbLkLt2ZG4C3kOkXFKH1HiT2RnHtFWcI/gAOsZl9isVHtgUlSnJZgQPP46k+smqDMPMXsMqcLaLYX7jOnsV2A+AFTX7auuVgCNDB6gyD7CKmFsDYAc9Op3NNK0hj91iMHUF4+wy2WCgszwHyjMcpOsDoBIHrO5qDCcKvYuxbtkhVtMwLMTJcsZOn1mQQDP2iwnSjYFEeEwqlAAAuwGgArRiyW1GKdaFwVisP3ilTpzB3g+lM7kyWYEkgBoggxsRqCDVqvIrNcdILVvKxZyxBgA5j4ROxiOZ3/APNTYhlQSz5R5mfnNVMPw/Jm8RKtuI5dJ/lVfi+HdiGXUARA333j9bVMJW4peRwMrSQfukaHzPpU/Cn/AHcA6gkAcjzH6FDVw1wmAje40Z4dhTbU5t23G+n6NSeoCBO0nZa1iQHuZluAkm4kajoQQRAgbjTrXNMThXwd5rTgtMZWBhWUnRo1/kQa7c9xU3YAdCfl+vdWK7WcKt4i0XRgLlokpp9YblT5HKNetSrWKM1abO2PICDM/g2OiknJInoNdT7pro3Y+yChuMPEy7yZysxMeQgCsJwvBm7bQqIIbK/lMEN7ASPYK6L2YuKe8VSCFCDQbDxD27UY7HEf9Wyq/XfUt2eA2EfOiQTMj6wM7yGn4U+zwTCoSUsWlJMmEUa+kRRClTiSe5wUXb+PE8ArifaY/wDN3j/bPyFdUtLjALj3GQyDltKBIPKHMR8a45jcLfS63fqUYkkqR1J2PMedJycmdj6WotjcguWwwhhIqbAcIW6yLMDXMZ1yLqSfLaJ5mo60HBMOVQvkzMRmyjcokwv+JveAanFy06GsOxOOzCvD7c94gBCK4VLY8MzbRpZhrrmkz11nQUD7R8Vtn9yLuihg6p4VzSIXTeNZ3/CpsTxg20d7nguX2hIJ0thEBeDqJyx7ulZDitnK+YbN8x+prYfxsThotvtbz1NJw/tLcy5UKhVAUMEAZmganMT8taL8Hx+LxF1ba3DG7nJbhU5n6nu8657w9gLiz1/DSupdn7fc21dT4mhiesjQekH51kdm3dzrt6OPTXX3dTaokACZIEToJ92g9lKKp4fiqNAbwn3j3/nVyaob8zkSVBTzUSV6aiEaTXkV47KurEAeZiqOJ4pbAIQktBggaTy3oqEvRVvhzeMjqKyuHxtxriguTLCR5T0Fabhx8Y9DVsYIcSG5UyAmlmqNzTQaUTLSUtXkU0U6amTFFNpxevJqLkzP8TsuHZiCQToeUch5RQ3EozI4UEkqwHqRpWzC1BjWhY6mrhvEjo2JzbszdPeNbMqXUgjmHWZH/cK1vYy6VxV+ydxbQ78wTPwcUE7QomHvWcSBAa4FuQOo0b1gEeenSmdisfPEMzad7nHtOoHuEVdODU3asDUIcoHjn9idUpl+8ttS7sFVRJJ2Ap9ZztnwO9jLaW7V0WwHlwQYYRpt0PLz8qYZx8aqzAMaEzvG+3udjbwqZoP1iGJnkQo1rHcRxt28+a8xL7eIZSB0iBAotjeyV3DPl72V0JYXDa08/lPwoFjkBaA7sVJEs/eLA2IMTS3Ujlp6DSHB1i5k+FwmYjN9XnG88l8id/Ia1oDiltoZMDQMRz0gW1+Xv5nTM4fEugjN8B1n1+NeXrpcyxmNug9BVldFHEplxZsj/d1BfHMc168ztpHhAGwUcv151Ve+SqqfszHoeVMdpJPUmvXXaOYB/XtpoJiiig/qSYHLnAYSDp7eRro/AcTmt5Tuhj2bj8vZXMRW07JYvOxHMrqPMH8pNJcENcewV9Oynscib5OFOQCGXUTGvPzpYHENafI8gE6jp5iruAabakMZjXWdtNjtt5VV40hhW0naRz57fz51QN4M5FR/FMXcFyFYqIGm38+VQPxO4QBmjSJG58yetecYPiXrlg+oP86ooCdgT6VYdSI+45JkmT1OtRzVpMDcbcR6yflNTXOGhUZiSSB5Ae4TPwqNwEKMr4D+sT1+QNavhrzcEbQaynDRNxfb8jWr4TrcPkv41KcuJLfgZXQSoPl8aTwoLEwACSTsANzUjrld16MT7G8Q+ceygPa+5GGIJIRrlpbpHK0bi5z6RofWluKYiSvNSNuIXLq95bLWrBIW2Qga9eJMAoH8NtDyLAkjXwip8Zns3MOq3blw3bmRrb5GlMpJcEKCuWBzjWiWIw1u5bytHd6EEEqABqGV1IyxGhBFZzHXrdu3cfD5u8uMllcVddnEPOZluXGJyIBMiFJIiaBLwxg+JJduXUthiLRCs8DIX5qDMkjnpzFEUFYt8VbRUwdhntWVTMbq/wBbekkZbS7szsD4xyEjSCYOE8Va1ZBViqXbgz3GLPbwyNIVZYnNdMSZ0BIzROtahVzeJdQsyBlLKAWUESAdpG4mOdUuIX0J7vMM4hisiQpkSRyBrK4DiS2Ld25ZRiLt85r9wMUS3mCJdZiJuTGeBoM2sVRTGi331yxLvdvC2t15ywFAFxrjCD4g7QNPQRVgIbYc4qcPctXEuspQQHhvEjaFdtQ0xFY1b5si1cT6wuFgTv4OfowaSOtW+MYkMq4dGJGXvGvNAN5lDAETEgkQDrOkcpoPcz4dBztGN5OVpj01Ee6rWRzNeBR+B6Pc69wTjFvE21dSMxEkfP8A8cqJEVwvh3Eblh89to6jkf5+dbfCfSLbCjvgFb26+hAI+VPVlfrgzBqdDkwk0LHxLvaLsPbxB7xb72onQ6rH4VguK9n/ANm8XeC4Jyzrrpy5EUb4v2/tuRlll6agAe4yfM1meM8fS84MkKo8I1nzJ8z+FXcLsN8mX0LalcgHSebqV6q47EhRlH1j8BUF/iBOiCPPnVEms6Y/Jnay5xVLPKu4TDFspEec9CSPZsaZhLIdbnUAEeuv5Ve4bdAt6/ZLe7f8a0ATAze0FXEKkqdwYq5wXHdzet3Psgw3906H3TNQ8Q/rG9nyFRIoB8WmnMe7TpVTUupnd+EMpt6jY6HyIB3Go3qZ7RdxzVNdebdJA1ArnHZTFWrltrdw20uLqL+XxhF1MOIKsBtMiORrcDjtpFVnPdK8tbHiJNoLPeOhUFJOmkySIJmst8mY8mPaaEfxsTkJBH1hr7OnpVjhVwC2AWAMncgc/wCdCuK8btNbtMQ4LkMq5SWyE5QxA+qCSIneat9n+KW3DWw2qkmdlIOmhO+oPu0mp8SlQn3q/eHsM/Kose/7t9Dt0jn51HieK2bbFXeCFzHcgDzOw2PpGsVWxPFbboyLmzFVJGUyoMEZhusjmdOUzpVAJJkHCkm57DWu4OkBjHMVkOCXQ1xgsyF1kEaEiN46VueH28qDz199aMS29+0VlNLUp8Utw6vyYZT6iSPhm9wqncRWBVgCCCCCJBB5EGjGPs50IG+6/wB4aj8vbQhCGAPX9e+jUJRuRjNioNscAwq7WU01AMso9FYlR7qIuBsQCOh2p4FNas9x3MSkSDAkbHmK9cAiIEdOVMWpYokSG4RlMjSDp5RtQt0EZSAR0IBHuovdUZTOgihUVdZBJgF7aPincE5reUEdDlOsHkQwgj7prFXbhDPB0Jb2ia0nGMT3WLd1Mh7ZB/8A2KsAe8L76yopuR1KAAToaDA65GdjYIFRV4ygiCJFe0qROvUH4nAgAsvLcH8KH1qhw5ntNczAATpz8/SgD4B5gQR1pqP4JmHLiBNqJUpUUw+AA1bU9OX86o4oQ7RoJpgcE0It8bILMWHv5Q4IkMI9DyNRhzEVav4bJbViPEzfDLpVOrxC0eRH3bhZix3NS25uMqhWZyQqhdSxJ0EdZNV60XYC2G4hYBEx3h9otOR8aqfeSx2i5a7GcCOIxD23BtrZguCASXzQEYHl4WkeXnW24pwaxndna491kVSxKmIMloKwJHhygRGgAmtFheHW7dy7cUeK6UL+qLlFUeIcOcuXQZgddxIPtpBYEzI+QmALmEkXVzsBdILmRnLBcurx9XnlAAknlpRXs9hrdlHcxIGmgWBAkKo65RJ1J01gAUrfDbhP1Y8yRRnDYVUQpvP1vOag1K7iZm77OzSWmXzkQOSwoECQBAPs8zVdbB0/eNmAIzaE6wSfEDLEgEkztyo7d4Pr4X08x+I3pWuD6+J/YB+J/KixI5kfZrCsGYDxTAmI15kkkknTWt2ogUK4PhVXUCANB68zReteBaF+8z5Gs1FQXFWslw/deWHk32h+PtNGqrYzDh1y7HdT0YbH9davkTctSqNtNwU1Q33yqzQTAJhRJMcgOZp4bcHQgwR0IrzNXPIozVd9THH6SuHgkE3QRoQbZkHpvTh9JvDvv3B//NqC/SR2N7wNjMMv7wa3bY+0B9sD7w5jn61yu0ikSSdJnQwNPCSYOhOkVrTHjcWIlmYHmdvb6R+GspHeXBodTaeNq9wXarDXRKd6w+93TheWuYiANa50vErFjD2rtvCYe6xJS47K/huQGAUEwPCd45GqeJ7TB4FzDrcUGYN68UmOQzZR6AVPojwJHqGabtJiLL3y1q4r5xmKgzEAAnTrFCqCJxu0plMIinbR7m3TUxTz2jH8Bf8Areltp2vidXT/AFBFQBu/1DFKhA7Rr/AU/wCNxr7KQ7SL/wCnT/MufnUfx3j/APE8XzC9KhJ7SD/06ex7n4mrFnj9tjJsKFEZmzXCQTMCJ11ETUfx3kf4li+ZeoNdtMXKxqSfzq7Y7S2IfPhvFl8EO5GeftaiBHrUVntBbLFjhBmCnKRdurHmddRE1fHhdTzE59didaF3L/FLOa1I+xB92hoJaWWAgmeQ3NWLvHrRUj9mWMxMG9dkmN99vKqycWtZl/cBIIkrcudd/FO1OKEzGmdVFSa5hGVoaFEEyZKgAE7qCeXStV2NyYO7+1Oe/HdlQMOO8KliurDQjQEbc6A9/cYXLq4N71q3mVrgN1rQEaksqgLoZmRVG3xu0uq4NFPUXbwPvDTyo9M1zKvqCwoTqtz6T8Cpgi6CNwUII9hpn9KOA/8Ay/5f/wAqwmC7QJiriWLmDtOrHV7jXGdUAlmFycwhQTvWQvlC7lAQuY5ATssmJPpVRgTyIje07UfpP4f1u/5f86Mdn+1NnGl+4W5lT6zugVZOyzOrc4rkPAeBjG3ktWMxGVWv3WAhFYAMoWIBBEKRqdeQrtXDOHW8NaSzaXKiDTqTzYnmxPOlZUxpwO5dCx/UvhqciyQBuarrRfhmH+2fZ+dJxpvaoxm2i5esWsqgVLSr2uiBUxxUqVKphBPE8Mf6xRqBDAc16+o+I9lDgZiNfOtNQHimFZAzW4gydZIRvvQNck7gbfLLnxXyI3G9cGZDtz2rXA24SGv3B4F5KP4jDoOQ5muGtdaSW3JluUkmfEOY8q6bxT6N7+IuveuYxWZzOttjA5AeLQDYCq4+iO4f/u0/y2/3VbG2NFq4MGJ6mR4HFy3ewxHjvLmQfZDpLLGujGCvpQW6ANAZG/p5Hzrptn6J71tldMWgZSCD3bbj/FWY7ecKTC3+6VAreJywZz3iucwOUrlXKZXQmYHQ01XVjwZUqR3AXCnwwcnFLdZMpgWmRGzyIMurCInSOlbbGcHwOJs8Pu4e1cspdxSYVwWQu6kibhYL9fXfbyoB2K4jZw9zEXLpQOMJeFksgcftBy5IVlInfcRvWmu9ombB8Ou4vMHTHLdJFjulaykHMuRFR/8ADJq8rAlrszZNziqZrkYJbhteJZJS6VGfw+LQcoohhuyWAH/DxdvYjPjEtnu0W3oztGbvG0VB92GJqzf4nw+3/wAUuW8b3j4xLuS2LF1ApdywUu431jYDTflVF+0GGN7g7954cKloXjlfwFbkkfV8Wn3ZohHYHshY7rE3Xt4vEG1jHwy28PlzZUE9437tvTkNaC37eBs32W5Zxy28i/u3a3buLcnmSkMkbHKDM1DieJk4289rEPZt3b7k3VLrFtrhIcosMYBmImrn0gcUtYm/aazcN5beHtW2uFXXM6BsxhwG1mZPWiEPN2Hw37ZetA4h7dvBjErbQobzsQv7sNkIO/JZoRf4HhmxOEsixjsP3163bcYgIJRnVSyNkWG15qRUfbXjqXsWl/C3W8Ni0mdc6MGVIYagHfntRlu0WHW1w22+La+9nFreuuyXvAkqSsuJYrqPDO1EIJsdm7LNxUFrn/JBza8S65bjIM/h8WgG0UTwvZrhw/4favDFG7jERiUuWwiZ2ygwbZ0OpiZHOpsVxHAWk4nct4zvGxqv3dvubqMC10tqxBWNdyQfIbVXucbwxu8IvLcLfstqyt9RbuTbFtgS0lYYeKPDO3mKISLC4Jjh+KYU37gtYJne2gKKGfvDbJchZYFVHhkCawwNdEv8QwFu3xQ28Z3tzGBu7trZvIATdLhczrqfF0A03rEcLW0Lqm/ORWGdBmDMB9gEA5Z2JO2tEIR4ZeRUu37gKhgLCi2FU+ISxAOkhVAP96glwMAA2kageTazNdTv/R82Jt2yt4Wl8dwIbbMQbr5tSWBMLlXUTpXmC+i17bFhibT+Fli5YLASImC0ZhyNL9VPeX2N7TLdiO1D8Pulbqt3NzKXWNR924Ad9DtzFdwtXkuKHRgysAVYGQQdiDXM/wCia4NTi0bb61tjtH9vyj0rY9jezeJwxa095LloksqqjL3ZJkhZY+H+zSMoRzanmXQle5p8Fhc58hv+VG0WAANhTLNoKABUtOx4wg+Yt23Ge0qVKmykVKlSohFXhFe0qIQBj+GlPFbErzQfZ818v7Pu6VDYMiRqK0lDsTw8El0hWO4+y3r0PmPjWbJhvlYxMlcGUyKznarsjYx/dm6zo1uYZInK26nMCCJE+/rWizQcrAq3Q9Oo6jzFek1mtkPzHcETnTfRNhP41/8A0/8AZVjEfR6rWUwzYq+1pGLIh7vwswgmck+yYrfU1hTBmf3kbFnNP6KMP/Gvf+z/AG04fRThv497/T/210jLTWSo9Z/eGxZzkfRThP49/wD0/wDbU4+inCER31+N/wD6Uz65JrdZDUyCKj1snvJ9NZz5volwf8e//p/7K8/onwn8e9/p/PJW/d6apo9d/eHprMAfomwn8e//AKf+2m/0U4UbX7/+n/trohqJjR67+8kY1mCH0WYUGe+vTynuyJ6wVg+nnTl+jTDZkZ7t5wmUBT3YBVTOUwmo399boGvctV9d/eHprPbQqwKiQVfw+DLatoPifyqUQt1IJA7kVmwX0HtNFLNkKIFOtoAIAin1sx4wv7iGctPaVKlTZSKlSpUQipUqVEIqVKlRCKlSpUQkF6wriGAI+R6g8jQ+/gHXVTnHQ6N/1bH2x60WpVRkVu5IYjqZ3PBggg9CIP8AP2U/NRu7aVhDAMOhAPzqlc4Wv2WK+X1h7jr7jWdtOf8AKY0ZPeUg1ONOfh9wbZWHkYPuOnxqN0cbo3sGb/tmlnEw8S4cGexTWemtcA+tp6yPnTe9T7y+8UsqZbcImSkqU4XV+8PeK9CsdlY/4T84oCH2hYjajZZq2uCc/Zj1IHymp7fDD9pvcPxP5VcYWbxIORRBgSKt2cI78oHU6fzNFLWFVdhr1Op+O1WKcmmA7MW2U+JVw+EVNdz1P60q1SpVpAA4EUTc9pUqVTIipUqVEIqVKlRCf//Z", quantity: 0 }, 
  {name:'Overnight',  price:750, img:"/img/2.jpg", quantity: 0 },
  {name:'Tamma',      price:1500, img:"/img/3.jpg", quantity: 0 },
  {name:'ไปยาล',     price:1599, img:"/img/4.jpg", quantity: 0 },
  {name:'Too nice',    price:1699, img:"/img/5.jpg", quantity: 0 },
  {name:'ท่าช้าง',  price:1890,  img:"/img/6.jpg", quantity: 0 },
  {name:'Beer lab',      price:675, img:"/img/7.jpg", quantity: 0 },
  {name:'Warm up',     price:1250, img:"/img/8.jpg", quantity: 0 },
])


//เก็บ list การจอง 
const list_local = ref([


]);


//function
function list_local_control(name, quantity) {
  const existingItemIndex = list_local.value.findIndex(item => item.name === name);

  if (existingItemIndex !== -1) {
    list_local.value[existingItemIndex].quantity += quantity;
    list_local.value[existingItemIndex].price = list_local.value[existingItemIndex].quantity * travelList.value.find(item => item.name === name).price;
  } else {
    const item = {
      name: name,
      quantity: quantity,
      price: quantity * travelList.value.find(item => item.name === name).price
    };
    list_local.value.push(item);
  }
}


function incrementQuantity(item) {
  item.quantity++;
  item.price = item.quantity * travelList.value.find((travel) => travel.name === item.name).price;
}

function decrementQuantity(item) {
  if (item.quantity > 0) {
    item.quantity--;
    item.price = item.quantity * travelList.value.find((travel) => travel.name === item.name).price;
  }
}

function removeItem(index) {
  list_local.value.splice(index, 1);
}



//pop up

const form_costumer = ref({
  name: "",
  phone: "",
  date: "",
  time: ""
});

const showPopup = ref(false);

const totalCost = computed(() => {
    return list_local.value.reduce((acc, item) => acc + item.price, 0);
});

function displayPopup() {
    showPopup.value = true;
}

function togglePopup() {
  showPopup.value = !showPopup.value;
}


</script>



<template>

  <HelloWorld v-if="showPopup" />
  <div class="overlay" v-if="showPopup">
    <HelloWorld />
  </div>

  <div class="header">
    <H1>รายการสินค้า</H1>
  </div><hr>


  <div class="container text-center">
    <div class="row">
      <div class="col" v-for="(i,index) in travelList" :key="index">
        <div class="card" style="width: 18rem;" >
          <img :src="i.img" class="card-img-top">
          <div class="card-body">
            <h3 class="card-title">{{ i.name }}</h3>
            <p>ราคาโต๊ะ : {{i.price}}</p>
            <h6>***จำกัด 5 คนต่อ 1 โต๊ะ***</h6>
            <p class="card-text">จำนวนโต๊ะ 
               <input type="number" class="cout_value " v-model="i.quantity">
            </p>
            <a class="btn btn-primary" @click="list_local_control(i.name, i.quantity)"> จองโต๊ะ </a>
          </div>
        </div>
      </div>
    </div>
  </div> 

 

  <h1 style="text-align: center; " v-if="list_local.length>0" class="header">รายการจองโต๊ะ</h1>
  <div class="list_cout text-center">
    <table class="table table-hover" v-if="list_local.length>0">
      <table class="table">
        <thead>
          <tr>
            <th scope="col">ลำดับ</th>
            <th scope="col">ชื่อร้าน</th>
            <th scope="col">จำนวนโต๊ะ</th>
            <th scope="col">ราคา</th>
            <th scope="col"></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(i,index) in list_local" :key="index" >
            <th scope="row">{{index+1}}</th>
            <td>{{ i.name }}</td>
            <td>
              <div class="quantity-controls">
                <button type="button" class="btn btn-danger"   @click="decrementQuantity(i)" :disabled="i.quantity === 0"> - </button>
                <span>{{ i.quantity }}</span>
                <button type="button" class="btn btn-success" @click="incrementQuantity(i)">+</button>
              </div>
            </td>
            <td>{{ i.price}}</td>
            <td>
              <button type="button" class="btn btn-danger" @click="removeItem(index)" >ลบรายการ</button>
            </td>
          </tr>
        </tbody>
      </table>  
    </table>
  </div>  

  
  <div class="contrainer_costumer " v-if="list_local.length>0">
  <div class="form_box"> <h2 style="text-align: center;">กรุณากรอกข้อมูล</h2></div>
  <form>
    <div class="form_box">
      <label for="name">ชื่อ-นามสกุล </label><br>
      <input type="text" id="name" class="form-control" v-model="form_costumer.name" required>
    </div>
    <div class="form_box">
      <label for="phone">เบอร์โทร </label><br>
      <input type="tel" id="phone" class="form-control" v-model="form_costumer.phone" required>
    </div>
    <div class="form_box">
      <label for="date">วันที่ </label><br>
      <input type="date" id="date" class="form-control" v-model="form_costumer.date" required>
    </div>
    <div class="form_box">
      <label for="time">เวลา </label><br>
      <input type="time" id="time" class="form-control" v-model="form_costumer.time" required>
    </div>
    <div class="form_box">
      <button type="button" class="btn btn-success" @click="togglePopup"> ยืนยันการจอง </button>
    </div>
  </form>
</div>


<div v-if="showPopup" class="overlay">

  <div class="popup">
      <h2 style="text-align: center; color:green ;">ยืนยันการจองสำเร็จ</h2>
      <h3 >รายละเอียด</h3>
      <p><strong>ชื่อ-นามสกุล:</strong> {{ form_costumer.name }}</p>
      <p><strong>เบอร์โทร:</strong> {{ form_costumer.phone }}</p>
      <p><strong>วันที่:</strong> {{ form_costumer.date }}</p>
      <p><strong>เวลา:</strong> {{ form_costumer.time }}</p>
      
      <table class="box_table">
          <thead>
              <tr>
                  <th>ลำดับ</th>
                  <th>ชื่อร้าน</th>
                  <th>จำนวนโต๊ะ</th>
                  <th>ราคา</th>
              </tr>
          </thead>
          <tbody>
              <tr v-for="(i, index) in list_local" :key="index">
                  <td>{{ index + 1 }}</td>
                  <td>{{ i.name }}</td>
                  <td>{{ i.quantity }}</td>
                  <td>{{ i.price }}  บาท </td>
              </tr>
          </tbody>
      </table>

      <p><strong>รวม:</strong> {{ totalCost }} บาท</p>

      <button class="btn btn-danger" @click="showPopup = false">ปิดหน้าต่าง</button>
  </div>
</div>



</template>


<style>
*{
  padding: 5px;
}
.header{
  text-align: center;
}
.card-img-top{
  height: 100%;
  padding: 25px;
}

.col{
  padding: 10px;
}


.contrainer_customer {
  justify-content: center;
  align-items: center;
  margin-left: 20%;
  margin-right: 20%;

}

.form_box{
    justify-content: center;
    align-items: center;
    padding: 5px;
    margin-left: 30%;
    margin-right: 30%;
}


.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
}


.popup {
  background-color: #fff;
  padding: 20px;
  border-radius: 10px;
  width: 70%;
  max-height: 80%;
  overflow-y: auto;
}

.header{
  padding: 25px;
}

</style>