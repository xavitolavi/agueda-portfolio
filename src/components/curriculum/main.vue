<template>
	<div class="curriculum-container">
		<div class="top-container">
			<img class="desktop" src="@/assets/ague-cv.jpg" alt="Ague CV">
			<div class="main-text">
				<p>Hi! I am a passionate illustrator, UX-UI and graphic designer based in Spain.
					My expertise extends beyond visual arts as I hold a strong background in corporate communication and
					copywriting.
					Through my artistic and written skills, I work to create beautiful and purposeful solutions for every project I
					undertake.
					Highly commended for my versatility, speed of learning and methodical approach to projects.
					Capable of working both in team-oriented and independent tasks.</p>
				<p>
					<img class="mobile" src="@/assets/ague-cv.jpg" alt="Ague CV">
				<ul class="studies">
					<li><span class="dates">2022 - 2023</span><span class="study"><span class="work">UX UI Design</span> <span
								class="bar">-</span> <span class="company-desktop">CODERHOUSE Accademy</span><span
								class="company-mobile">CODERHOUSE Accademy</span></span></li>
					<li><span class="dates">2021 - 2022</span><span class="study"><span class="work">Graphic design and Web
								Development</span> <span class="bar">-</span> <span class="company-desktop">ESPAI</span><span
								class="company-mobile">ESPAI</span></span></li>
					<li><span class="dates">2017 - 2021</span><span class="study"><span class="work">Communication and Cultural
								Industries</span> <span class="bar">-</span> <span class="company-desktop">UB</span><span
								class="company-mobile">Universitat de Barcelona</span></span></li>
				</ul>
				</p>
				<div class="skills mobile">
					<ul>
						<li>English: fluent</li>
						<li>Catalan: native</li>
						<li>Spanish: native</li>
					</ul>
					<ul>
						<li>Figma</li>
						<li>Procreate</li>
						<li>Wordpress</li>
						<li>Office Suite</li>
						<li>Adobe Pr / Id / Ps</li>
					</ul>
				</div>
			</div>
		</div>
		<div class="bottom-container">
			<ul>
				<li v-for="exp in experiences" :key="exp.id">
					<div class="dates">
						<p>{{ exp.startDate }}</p>
						<p>{{ exp.endDate }}</p>
					</div>
					<div class="desktop-place">
						<p class="title">{{ exp.title }}</p>
						<p>{{ exp.subtitle }}</p>
					</div>
					<div class="desktop-knowledges">
						<p v-for="(skill, index) in exp.skills" :key="index">
							{{ skill }}
						</p>
					</div>
					<div class="mobile-skills">
						<div class="place">
							<p class="title">{{ exp.title }}</p>
							<p>{{ exp.subtitle }}</p>
						</div>
						<div class="knowledges">
							<p v-for="(skill, index) in exp.skills" :key="index">
								{{ skill }}
							</p>
						</div>
					</div>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>
import experiences from './schema';

export default {
	name: "CurriculumView",

	props: {
		selectedCV: {
			type: Boolean,
			default: () => false
		}
	},

	computed: {
		experiences() {
			return experiences;
		}
	}
}
</script>

<style lang="less">
.curriculum-container {
	margin: 10rem 8vw 0 8vw;
	display: flex;
	flex-direction: column;

	.top-container {
		display: flex;
		flex-direction: row;
		justify-content: center;
		gap: 10rem;

		img {
			height: 550px;

			&.mobile {
				display: none;
			}
		}

		.main-text {
			width: 35rem;
			text-align: justify;

			.studies {
				margin-top: 10rem;

				li {
					text-align: justify;
					display: flex;
					margin-bottom: 1rem;

					.dates {
						color: rgba(0, 0, 0, .5);
						width: 8rem;
					}

					.study {
						.company-mobile {
							display: none;
						}
					}
				}
			}

			.skills {
				margin-top: 5rem;
				display: flex;
				gap: 7rem;
			}
		}
	}

	.bottom-container {
		margin-top: 7rem;

		ul {
			display: grid;

			li {
				margin-bottom: 5rem;
				display: flex;
				gap: 5rem;
				justify-content: center;

				.dates {
					text-align: left;
					color: rgba(0, 0, 0, .5);
				}

				.desktop-place {
					text-align: left;
					width: 18rem;

					.title {
						font-weight: 600;
					}
				}

				.desktop-knowledges {
					text-align: left;
					width: 30rem;
				}

				.mobile-skills {
					display: none;
				}
			}
		}
	}
}

@media (max-width: 768px) {
	.curriculum-container {
		font-size: 14px;
		margin: 200px 30px 0;

		.top-container {

			img {
				&.desktop {
					display: none;
				}

				&.mobile {
					margin-top: 4rem;
					display: block;
					width: 100%;
					height: 100%;
				}
			}

			.main-text {
				width: 100%;

				.studies {
					margin-top: 4rem;

					li {
						margin-bottom: 2rem;

						.dates {
							flex: 30%;
						}

						.study {
							flex: 60%;

							.work {
								font-weight: 600;
							}

							.company-desktop {
								display: none;
							}

							.company-mobile {
								display: block;
							}

							.bar {
								display: none;
							}
						}
					}
				}

				.skills {
					margin-left: 30vw;
					gap: 4rem;
				}
			}
		}

		.bottom-container {
			ul {
				width: 100%;
				display: flex;
				flex-direction: column;

				li {
					display: flex;
					gap: 0;

					.desktop-place,
					.desktop-knowledges {
						display: none;
					}

					.dates {
						flex: 30%;
						text-transform: uppercase;
					}

					.mobile-skills {
						flex: 60%;
						text-align: start;
						display: block;

						.place {
							margin-bottom: 3rem;

							.title {
								text-transform: uppercase;
								font-weight: 600;
							}
						}
					}
				}
			}
		}
	}
}</style>